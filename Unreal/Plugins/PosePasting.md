#PosePasting #PoseCaching

## Notes
Another route might be: Bake forward -> remove keyframes -> paste anim
Issue with this route might be that we will need to save poses on the fk-rig

```mermaid
---
title: Rig flow for blending to base pose
---
flowchart TD


    subgraph A[Setup Base]
        A0[Get bone names]
        A1[Get transforms for bones]
        A2[Cache the bone transforms for the default pose]
        A0 --> A1 --> A2
    end

	subgraph B[Blending to base]
		B0[Get current transform for bones]
		B1[Get user supplied weight]
		B2[Cache the Blend towards cached transform for later]
		B0 --> B2
		B1 --> B2
	end
	
	subgraph C[Offsetting Rig controls]
		C0[Apply user controls]
		C1[Apply cached blends]
		C2[Display the controls on the new location]
		C0 --> C1 --> C2
	end
	
	A -->|Using any animation and this rig as a layer we do the following| B
	B -->|Following graph needed to keep rig controls functional| C
	
```

```mermaid
---
title: Rig flow for blending to base pose 2.0
---
flowchart TD


    subgraph A[Construct Event]
        A0[Cache bone transforms for resting pose]
    end

	subgraph B[Backwards Solve]
		B0[Cache bone transforms for animation]
	end
	
	subgraph C[Forward Solve]
		subgraph CA[Blend To Base]
			CA0[Get user supplied weight]
			CA1[Blend between transforms from caches]
			CA2[Get relative transform of blend and animated transform]
			CA3[Offset relevant bone]
			CA0 --> CA1 --> CA2 --> CA3
		end

		subgraph CB[Apply User Control]
			CB0[Get relative transform between animated and resting]
			CB1[Get relative transform of control and relative animated]
			CB2[Offset relevant bone]
			CB0 --> CB1 --> CB2
		end
		
		CA -->|Ordering not relevant| CB
	end
	
	A -->|Using any animation and this rig as a layer we do the following| B
	B -->|Following graph needed to keep rig controls functional| C
	A --> C	
```
## Return to base Pose
- [x] <span class="blue">NamedTransformCache Plugin</span> to save poses
- [ ] Add Plugin to <span class="blue">rig</span>
	- [x] Cache the reference pose
		- [ ] Test
	- [x] Add a weight to blend back to the base pose
		- Make sure in the forward as the first step so we can apply other stuff later
			<span class="red">I did that, but that wont work because the controls set stuff, so I put it last</span>
		- [ ] How do we solve the above issue, and is it an issue? We should test on an actual animation
		- [ ] Make it keyable as a control
		- [ ] Test blend back
- [ ] Rig changes to the <span class="blue">Picker</span>
	- [ ] Add weight to the picker
## Paste Pose
