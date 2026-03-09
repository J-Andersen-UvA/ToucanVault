### inputData
- [x] Make sure we have csv Blendshapes (<span class="blue">blendshapes</span>)
- [x] Make sure we have the post animation (<span class="blue">skeletal</span>)
- [x] Get the difference and foot detected output to every folder (<span class="blue">timingOffset</span>)
- [x] Get the animation range for every rpm animation to every folder (<span class="blue">animRange</span>)

### Job queue
- [x] EUW containing:
	- [x] Joblist
		- [x] joblist done
		- [x] joblist to do
	- [x] Process next 100: All plugins to execute the pipeline
	- [x] Reset pipeline
		- [x] Sequencer cleanup
		- [x] Remove files (maybe will help with recordings, perhaps test first without doing this so we can test if it helps with the cache)
### Unreal prep
- [x] Import script
	- [x] Post animations into unreal engine
	- [x] CSV blendshapes into unreal engine (test if works with fix of name NumProperties To BlendshapeCount)
	- [x] get anim range
	- [x] get timing offset
- [x] Get retarget on Vicon pc from unreal pc, by hand ofcourse
- [x] By script Retarget post animation onto palmer
- [x] Why is it 120fps??? Because it was exported at 120fps from shogun post, no issue here.

### sequencerPrep
- [x] Script that uses all plugins
	- [x] open prepped sequencer (check skeletal add. cant we reuse a bp actor from prepared sequence?)
	- [x] add csv to sequencer
	- [x] add retargeted animation to sequencer
	- [x] Move anim
	- [x] Move csv
- [x] Update llf
- [x] Set csv name on palmer actor
### timingAndRange
- [x] Apply animation range
- [x] shift the skeletal animation based on timing offset
- [x] Shift the csv take to end at the range end
### outputData
- [x] Make export script to get final animation out of unreal engine (use the py that we are already using for its settings)
- [x] Set metadata for CC
- [x] Set jobs bool

- [ ] Do I care about the tposing at the beginning of some anims? We can maybe cut after processing? (example E:\Recordings\2025-11-18\M20240925_1925_251118_1)

```mermaid
flowchart TD

    subgraph inputData
        a1["timingOffset 24fps"]
        a3["animationRangeFrames 24fps"]
        a4["animationPost"]
        a5["csvBlendshapes"]
    end

	subgraph UnrealPrep
	    a4 --> b1["importScript (cpp api)"]
	    a5 --> b1
	
	    b1 --> b2["unrealEngine"]
	
	    b2 --> c1["retargetToPalmer (cpp api)"]
	end

	subgraph sequencerPrep
	    c1 --> d1["openPreparedSequence (python api -> cpp plugin)"]
	
	    d1 --> d2["addAnimationToPalmerSkeletalMesh"]
	    d1 --> d3["addCsvToSequence"]
	    d3 --> movePlayHead1["movePlayhead Forcing Update for llf"]
	end

	d4["setCsvNameOnOwningActorBp"]
	movePlayHead1 --> d4
	d4 --> d5

	subgraph timingAndRange
	    a3 --> d5["applyAnimationRange"]
	    a1 --> d7["shiftSkeletalAnimationClip"]
	    d5 --> d6["shiftCSVTakeToEndRange"]
	    d6 --> d7
	end

    d7 --> e1["bakeSequence"]

	e1 --> f1["exportBakeToHostPcFolder"]
	subgraph outputData
		f1
	end
```
