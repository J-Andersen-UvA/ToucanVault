### inputData
- [x] Make sure we have csv Blendshapes (<span class="blue">blendshapes</span>)
- [x] Make sure we have the post animation (<span class="blue">skeletal</span>)
- [x] Get the difference and foot detected output to every folder (<span class="blue">timingOffset</span>)
- [x] Get the animation range for every rpm animation to every folder (<span class="blue">animRange</span>)

### Unreal prep
- [ ] Import script
	- [x] Post animations into unreal engine
	- [x] CSV blendshapes into unreal engine (test if works with fix of name NumProperties To BlendshapeCount)
	- [ ] 
- [ ] Get retarget on Vicon pc from unreal pc, by hand ofcourse
- [ ] Retarget post animation onto palmer

### sequencerPrep
- [ ] python script that uses plugin
	- [ ] open prepped sequencer
	- [ ] add csv to sequencer
	- [ ] add retargeted animation to sequencer

- [ ] Set csv name on palmer actor
### timingAndRange
- [ ] Apply animation range
- [ ] shift the skeletal animation based on timing offset
- [ ] Shift the csv take to end at the range end
### outputData
- [ ] Make export script to get final animation out of unreal engine

```mermaid
flowchart TD

    subgraph inputData
        a1["timingOffset 24fps"]
        a3["animationRangeFrames 24fps"]
        a4["animationPost"]
        a5["csvBlendshapes"]
    end

	subgraph UnrealPrep
	    a4 --> b1["importScript (python)"]
	    a5 --> b1
	
	    b1 --> b2["unrealEngine"]
	
	    b2 --> c1["retargetToPalmer (python api)"]
	end

	subgraph sequencerPrep
	    c1 --> d1["openPreparedSequence (python api -> cpp plugin)"]
	
	    d1 --> d2["addAnimationToPalmerSkeletalMesh"]
	    d1 --> d3["addCsvToSequence"]
	end

	d4["setCsvNameOnOwningActorBp"]
	d3 --> d4
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
