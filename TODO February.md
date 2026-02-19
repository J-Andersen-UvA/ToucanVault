
### Implement CC into post processing pipeline
- [ ] How does the CC rig work with new skeletal meshes
	- [ ] Why is the face separated from the rest for the body rig
	- [ ] Should I add the face rig immediately to the pipeline?
	- [ ] Why face rig not here
- [ ] Test with current pipeline, is it modular enough to support the rig
	- [ ] Do we need to automatically open the picker?
	- [ ] Does it work with queue code
	- [ ] Does it work with midi code

### Implement new pipeline for recording
- [x] Recording project to 5.7
- [x] Shogun Live -> UE Vicon avatar
- [x] Retargets UE Vicon
	- [x] RPM
	- [x] CC   (<span class="red">Pretty hard, take time to do this</span>)
		- [Vicon MOCAP to MetaHuman | Shogun Solve and Retarget Guide](https://www.youtube.com/watch?v=KnRPx-b5Rx8)
			Speaks about, Vicon -> mannequin through shogun post, and then ik retargeter in unreal. Maybe thats a good route?
		- Maybe we cant retarget to RPM and CC at the same time. This is due to the solve of Vicon, the CC avatar wants the wrists to be rotated, but the RPM wants the elbow to be rotated. [[CC Avatars#^7e9cc1]] 
			You would get a twisted balloon for RPM if we used the solve for the CC.
			Apparently, the twistbones are to mimic what MH is doing. I cannot find the twistbones in the CC blueprints.
	- [x] Watch UE IK retargeter and Vicon retargeter videos, gather info:
		- Schouders te hoog van CC, doe schouders omhoog van Vicon in IKretargeter.
		- There are bone settings in the IK_rig
		- If you begin from t-pose in animations, you can use that pose as a source to do the retarget from, making the final retarget more closely mimick what was intended.
- [ ] Implement in UEpython script
	- [x] New branch?
	- [x] Add RPM + CC to takerecorder
	- [x] Export stuff for CC to new folder
	- [x] Vicon Recording in UE
	- [ ] Anim export direction?

### Old anims to new avatar:
Step 1. Gathering the input
- [x] Compile overview
	- [x] Do we want to do the following in a script, or are we going to do single folder with symlinks. <span class="blue">In a script resulting in a csv we can reference</span>
	- [x] Compile all vicon mcp files that dont have an fbx file yet.\
	- [x] Create hardlinks of the mcps in a single folder, for use in shogun post
- [x] Use automatic mcp -> fbx script (refresh how it worked)
	- [x] Use X2D to resolve dropped frames? <span class="red">Nah, just fill with interpolation</span>
	- [x] Autoskeleton for fingers? <span class="blue">Yes with SetMainFingerConstraints.hsl</span>
	- [x] Use auto fill gaps? <span class="blue">Yes, with AutoFillThenSolve.hsl</span>
	- [x] Solve
	- [x] Run conversion to fbx
	- [x] Update overview along the way? <span class="red">No, we will do it afterwards</span>
- [x] Move Fbx to shogun_post folders
	- [x] Move
	- [x] Update metadata
- [x] New project 5.7 (reallusion project kan ook)
- [ ] Basic fbx loader script maken die Vicon skeleton gebruikt
	- [ ] Hou ook in UE bij in een file waar we zijn met retargeting etc (status)
- [ ] Basic CSV loader script?

Step 2. Processing input
- [x] Vicon -> CC retarget maken met voorbeeld animaties
- [ ] Basic sequencer control tool maken, been a long time coming anyways
	- [ ] Create sequence
	- [ ] Save sequence
	- [ ] Get current open sequence
	- [ ] Load into sequence?
- [ ] Batch retargeting script of met present tools in UE?
- [ ] What needs to be done to bake csv blendshapes onto avatar?
	- [ ] Do we need a separate bake or can we use livelink during a bake (doubt)
- [ ] Make a foot move detection script (end of anim detection)
- [ ] Bake anim and blendshapes for every animation together

Step 3. Processing output
- [ ] Export tool out of unreal or by hand?
	- [ ] Update overview
		- [ ] Do we need to rename the retargeted_animation_fbx field, or add a key to that field "avatar:"
	- [ ] Export into ue folder with extra attached name or extra folder (CC)? Discuss with gomer what he wants for rclone