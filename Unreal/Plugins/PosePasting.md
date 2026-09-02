#PosePasting #PoseCaching

## Notes
Another route might be: Bake forward -> remove keyframes -> paste anim
Issue with this route might be that we will need to save poses on the fk-rig

```mermaid
---
title: Rig flow for blending to base pose 2.0
---
flowchart TD


    subgraph A[Construct Event]
        A0[Cache resting bone transforms<br/>FingersResting]
    end

	subgraph B[Backwards Solve]
		B0[Cache incoming animated bone transforms<br/>FingersAnimated]
	end
	
	subgraph C[Forward Solve]
		subgraph CA[Blend Animation Toward Base]
			CA0[Read user base-pose weight]
			CA1[Blend FingersAnimated → FingersResting]
			CA2[Compute correction:<br/>blended pose relative to FingersAnimated]
			CA3[Apply correction as bone offset]
			CA0 --> CA1 --> CA2 --> CA3
		end

		subgraph CB[Apply User Control]
			CB0[Get animated transform relative to resting transform]
			CB1[Get control transform relative to animated-vs-resting offset]
			CB2[Apply result as bone offset]
			CB0 --> CB1 --> CB2
		end
		
		CA <-->|Independent corrections| CB
	end
	
	B --> C
	A --> C	
```
## Return to base Pose
- [x] <span class="blue">NamedTransformCache Plugin</span> to save poses
- [x] Add Plugin to <span class="blue">rig</span>
	- [x] Cache the reference pose
		- [x] Test
	- [x] Add a weight to blend back to the base pose
		- Make sure in the forward as the first step so we can apply other stuff later
			<span class="red">I did that, but that wont work because the controls set stuff, so I put it last</span>
		- [x] How do we solve the above issue, and is it an issue? We should test on an actual animation
		- [x] Make it keyable as a control
		- [x] Test blend back
- [ ] Rig changes to the <span class="blue">Picker</span>
	- [ ] Add weight to the picker
- [ ] Make the splay control offset instead of set. 
## Paste Pose
