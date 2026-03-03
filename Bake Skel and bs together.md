### inputData
- [x] Make sure we have csv Blendshapes (<span class="blue">blendshapes</span>)
- [x] Make sure we have the post animation (<span class="blue">skeletal</span>)
- [ ] Get the difference and foot detected output to every folder (<span class="blue">timingOffset</span>)
- [ ] Get the animation range for every rpm animation to every folder (<span class="blue">animRange</span>)

### Unreal prep
- [ ] Import script
	- [ ] Post animations into unreal engine
	- [ ] CSV blendshapes into unreal engine 
- [ ] Get retarget on Vicon pc from unreal pc
- [ ] Retarget post animation onto palmer

### sequencerPrep
- [ ] python script that uses plugin
	- [ ] open prepped sequencer
	- [ ] add csv to sequencer
	- [ ] add retargeted animation to sequencer
	- [ ] 
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
	
	    d3 --> d4["setCsvNameOnOwningActorBp"]
	end

	subgraph timingAndRange
	    a3 --> d5["applyAnimationRange"]
	    d4 --> d5
	    a1 --> d7["shiftAnimationClip"]
	    d5 --> d7
	end

    d7 --> e1["bakeSequence"]

	e1 --> f1["exportBakeToHostPcFolder"]
	subgraph outputData
		f1
	end
```
