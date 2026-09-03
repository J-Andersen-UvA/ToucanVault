- [x] CV
- [ ] Paper alinea
Following motion capture recording, animations were post-processed in Unreal Engine using a custom animation editing pipeline. The goal of post-processing was to correct technical capture and retargeting artifacts while preserving the original linguistic performance of the signer. Rather than replacing the recorded motion, all edits were applied additively: the original motion capture data remained unchanged, and corrective animation layers were added only where necessary.

The most common corrections addressed four types of issues:
- **Retargeting differences:** because the virtual signer differs in body proportions from the human signer, some joint rotations appeared exaggerated or insufficient and were adjusted. This includes rotating fingers to appear more bended, and repositioning the hands to fix the arm rotations.
- **Marker jitter:** small inconsistencies in marker tracking occasionally caused shaking movements of the hands, arms, or body, which were smoothed.
- **Occlusions:** temporary loss of body markers or facial features sometimes resulted in frozen or unstable poses that were manually corrected.
- **Missing articulators:** tongue movements and certain oral components, such as sucked-in cheeks, are not reliably captured by the recording system and were manually animated.

Each animation was loaded into the editing environment together with a control rig that allowed frame-accurate correction of body, hand, facial, and oral movements. After editing, the corrective layers were baked into the final animation and the result was saved for inclusion in the dataset.


- [x] Rig selection method, change it to the faster method like in the forward picker
- [ ] Get rid of throat wrinkles
- [ ] Splay slider additive with offset instead of set
- [ ] Update splay slider based on values in sequencer
- [ ] Checkpoint en next todo swappen van kant
- [ ] says editing when not actuyally editing on load
- [ ] Curve sequencer heeft tools zoals mocap editing tools om curves minder noise te geven etc. <span class="blue">Zet dit in documentatie</span>
- [ ] Auto focus for all tools
- [ ] New tool to check what has been post processed
- [ ] avatar en anims meenemen naar huis voor testing
- [ ] Stylized avatar in CC? Voor signlab. Kopen?

- Post processing pipeline in unreal engine character creator fixes some eye related baking, so i changed my implementation to only alter the eye data in the post processing pipeline
	- [ ] Get CC post processing blueprint changes into my git
	- [ ] Add these changes to Galya's and Jose's machines

Pose library
- [ ] [[PosePasting]]
- [ ] Leaking?

Face:
- [ ] Focus not working
- [ ] Slider changes to aggresive for the ctrlz
- [ ] Not live updating anymore


- JamesDev
- [ ] Test audio driven lip sync?



### Demo render
- [ ] Cloth and hair physiics for demo?
- [ ] Scene
- [ ] Use mocapped camera