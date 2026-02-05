Step 1. Gathering the input
- [x] Compile overview
	- [x] Do we want to do the following in a script, or are we going to do single folder with symlinks. <span class="blue">In a script resulting in a csv we can reference</span>
	- [x] Compile all vicon mcp files that dont have an fbx file yet.\
	- [x] Create hardlinks of the mcps in a single folder, for use in shogun post
- [ ] Use automatic mcp -> fbx script (refresh how it worked)
	- [x] Use X2D to resolve dropped frames? <span class="red">Nah, just fill with interpolation</span>
	- [x] Autoskeleton for fingers? <span class="blue">Yes with SetMainFingerConstraints.hsl</span>
	- [x] Use auto fill gaps? <span class="blue">Yes, with AutoFillThenSolve.hsl</span>
	- [x] Solve
	- [x] Run conversion to fbx
	- [x] Update overview along the way? <span class="red">No, we will do it afterwards</span>
- [ ] Move Fbx to shogun_post folders
	- [ ] Move
	- [ ] Update metadata
- [ ] New project 5.7 (reallusion project kan ook)
- [ ] Basic fbx loader script maken die Vicon skeleton gebruikt
	- [ ] Hou ook in UE bij in een file waar we zijn met retargeting etc (status)
- [ ] Basic CSV loader script?

Step 2. Processing input
- [ ] Vicon -> CC retarget maken met voorbeeld animaties
- [ ] Basic sequencer control tool maken, been a long time coming anyways
	- [ ] Create sequence
	- [ ] Save sequence
	- [ ] Get current open sequence
	- [ ] Load into sequence?
- [ ] Batch retargeting script of met present tools in UE?
- [ ] What needs to be done to bake csv blendshapes onto avatar?
	- [ ] Do we need a separate bake or can we use livelink during a bake (doubt)
- [ ] Bake anim and blendshapes for every animation together

Step 3. Processing output
- [ ] Export tool out of unreal or by hand?
	- [ ] Update overview
		- [ ] Do we need to rename the retargeted_animation_fbx field, or add a key to that field "avatar:"
	- [ ] Export into ue folder with extra attached name or extra folder (CC)? Discuss with gomer what he wants for rclone