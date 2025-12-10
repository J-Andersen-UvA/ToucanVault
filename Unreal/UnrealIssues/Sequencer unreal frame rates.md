#Sequencer #UnrealEngine #TroubleShooting 

# Hell(p)

1. **Six different framerate systems** controlling different subsystems
2. **No unified API** to set all of them consistently
3. `DefaultFrameRate` silently controls AnimSequence creation but isn't documented
4. `PlatformTargetFrameRate` is protected, hidden, and influences validation
5. Sequencer DisplayRate is mostly UI-only
6. Sequencer TickResolution controls evaluation but is invisible in UI
7. Recorder works per-engine-tick if not overridden
8. ExportToAnimSequence doesn’t harmonize these settings

Baking reliably in C++ requires aligning:
```cpp
DefaultFrameRate
SamplingFrameRate
PlatformTargetFrameRate
TickResolution
DisplayRate
CustomFrameRate
ImportedFrameRate
```

---
# Further explanation

Below is a **breakdown** of every framerate system inside Unreal Engine’s animation + Sequencer pipeline — **what it does, who consumes it, and why it exists**.

---
# 1. **Display Rate (Sequencer)**
#### What it is
The “presentation” framerate for a LevelSequence.
#### Where it lives
`UMovieScene::DisplayRate`
#### Who uses it
- Sequencer UI timeline
- Curves displayed in the editor
- Frame number ↔ seconds conversion for user interaction
- Some evaluation paths (not recorder)
#### Why it exists
For artists to view/edit animation at a human-friendly framerate (film 24 / TV 30 / game 60).

#### Why it does _NOT_ control actual baking
Sequencer evaluation uses **tick resolution**, not display rate.  
AnimationRecorder uses **sampling rate**, not display rate.

---
# 2. **Tick Resolution (Sequencer Evaluation Rate)**
#### What it is
The internal high-precision time grid Sequencer uses for evaluating tracks.
#### Where it lives
`UMovieScene::TickResolution`
#### Who uses it
- Sequencer evaluation
- Control Rig evaluation
- Track interpolation
- BakeToSkelMeshToCallbacks (export system)
#### Why it exists
To allow sub-frame precision and arbitrary time coordinates independent of DisplayRate.

#### Why it matters for baking
If TickResolution ≠ SampleRate, the recorder sees timestamps like:
`0, 1/30, 2/30, 3/30...`
even if you _wanted_ 24 fps.

This <span class="red">mismatch</span> produces:
- <span class="red">Morph drift</span>
- “24 fps not a multiple or factor of 30 fps”
- Shifting transforms

---
# 3. **DefaultFrameRate (Engine Animation Settings)**
#### What it is
The sampling rate used when a brand-new **UAnimSequence** is created.
#### Where it lives
`UAnimationSettings::DefaultFrameRate`
#### Who uses it
- UAnimSequenceFactory (creation)
- Import system fallback
- ANY C++ asset creation
#### Why it exists
Historical reasons — legacy animations needed consistent frame sampling.
#### Why it breaks baking
If DefaultFrameRate = 30 and you want to bake 24:
- The new AnimSequence data model is initialized at **30 fps**
- Recorder tries to write **24 fps** keys
- → Error: “24 not a factor of 30”
- Unreal coerces to **30 fps**
- <span class="red">Morphs drift</span>

---
# 4. **SamplingFrameRate (AnimSequence internal sampling rate)**
#### What it is
The actual timebase used by the animation’s data model.
#### Where it lives
Private inside `UAnimSequence`. Accessed via data model.
#### Who uses it
- Animation Recorder
- Animation Compression
- Retargeting
- Playback
#### Why it exists
AnimSequence needs a consistent, fixed sampling grid for storing keys.
#### Why it's important
If this rate ≠ Export SampleRate → drift, resampling, mismatched timing.

---
# 5. **CustomFrameRate (ExportOptions)**
#### What it is
Optional override for the bake sampling rate.
#### Where it lives
`UAnimSeqExportOption::CustomFrameRate`
#### Who uses it
- ExportToAnimSequence
- AnimationRecorder.Init()
#### Why it exists
So users can export at arbitrary rates (e.g. 60 fps).
####  Why it fails silently
If AnimSequence’s internal sampling rate is not compatible, UE logs error and forces the closest acceptable rate (usually 30).

---
# 6. **PlatformTargetFrameRate (AnimSequence cooked target rate)**
#### What it is
An **FPerPlatformFrameRate** specifying desired framerate for cooking.
#### Where it lives
`UAnimSequence::PlatformTargetFrameRate`
Protected. Editor sets it based on platform.
#### Who uses it
- Cooking & compression
- Data model validation
#### Why it exists
To optimize animation for target devices.
#### Why it breaks export
If PlatformTargetFrameRate=30, and you try to write 24fps keys:
- Validation error
- Forced resampling
- Drift

---
# 7. **Timecode Rate**
#### What it is
For film/production workflows: SMTPE timecode.
#### Where it lives
`AnimationRecorder → FQualifiedFrameTime`
#### Who uses it
- AnimationRecorder when bBakeTimecode=true
- Sequencer slates
#### Why it exists
Film/Virtual Production.
