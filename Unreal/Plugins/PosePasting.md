#PosePasting #PoseCaching
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
