- [x] Check mocap setup for Debby
- [x] Meeting Anna
- [x] Verse?
- [x] session sequencer now bakes timecodes
- [x] New router?
- [x] Test if timecodes are exporting in main pipeline.
	- We had to save first in order to get the export to work. Such a stupid thing that we are forced to do. Why can we even export an unfinished asset???
- [x] Renders maken voor Rob/Jart.
- [ ] Viseme
	- [x] Add tongue and Jaw control to the viseme sliders.
	- [x] Add all visemes
		- 6, 7, 8 (skip), 9, 10, 11 (skip), 13 (maybe use V_Affricate instead), 14, 15, 16, 17, 18 (skip), 19, 20, 21, 22, 23, 24, 25, 26 (skip), 27 (skip), 28 (skip), 29 (skip), 30, 31 (skip)
			Some skipped because they are captured well by the system, or too similar in blendshapes to other oral components
	- [x] In oral component picker notify user to play with jaw triangle for 7, 9, 10
	- [x] Reset the controls for the jaw and tongue if nothing is selected (it stays stale from previous change, so maybe just make sure it always sets to 0 first and then apply changes?)
	- [x] Add jaw controls so we can combine the manual with the automatic ones 
		- fixed the jaw issue by parenting the manual to the automatic. The bone is controlled by the manual one. So the automatic can move itself (indirectly moving the manual one), the manual one can be moved by us, and then the bone is moved.
		- [x] Make sure the manual moves correctly when the auto moves (or the auto is moving incorecrtly for our example)
		- [x] Test on animations
	- [x] Update tongue UI when viseme slider is used
	- [x] Remove unused oral components
		- Removed components: 08_Open_gestrekt, 11_Kaak_omlaag, 18_Lippen_gesloten, 25_Prr, 27_Pm, 28_Bam, 29_Boem, 31_Pl
	- [x] Replace pictures with avatar pictures
	- [x] Clicking image means setting it to 1 if its already 1 set it to 0
	- [x] Turn off auto key zero for oral components when setting other values (maybe replace with notification that multiple components are non-zero), user should hold agency over this
	- [x] Fix update for sliders values, the issue is that all cards are checking it and therefore one is setting it to the newer time value which is what screws over all other cards
	- [x] Add "Add Rig" button. Changed to add rig from parent picker instead.
	- [x] Invert slider
		- [x] Ability to get current values of anim asset
		- [x] Add forward control rig, <span class="blue">Niet nodig</span>
			- All morph targets that aren't keyable in the face rig will make it really hard to get an inverse working. maybe we add a forward rig?
			- Actually, maybe just doing the <span class="blue">inverse in the forward solve first and then applying all the changes</span> will be better?
	- [x] Picker tongue en oral tegelijkertijd kunnen gebruiken
	- [x] Picker Notification should display after making changes as well, not only on sequencer change.
	- [x] Tongue picker moving, makes too many ctrl z backlog
	- [x] Rig CC5, interpolates between finger ctrls for smooth closing, dissabled this, but we should use it for the slider in the ui
	- [x] Splay handles for UI
	- [x] UI redo of picker
	- [x] Splay values fixen in blueprint
	- [x] We should learn what project to new parent does
	- [x] Splay zero, Splay key current
	- [x] Fix zero head_ctrl.local in skip list... <span class="blue">I used the script name: head_local. Found in The rig</span>
	- [ ] Get rid of throat wrinkles
	- [x] Splay from metacarpals
	- [ ] Update splay slider based on values in sequencer
	- [x] Zero now, sets ik of feet
	- [ ] Checkpoint en next todo swappen van kant
	- [x] zero jaw control
	- [ ] says editing when not actuyally editing on load
	- [ ] Automatic rig selection inside picker, we can maybe add function to the picker, and we use the sessionsequencer to find all pickers with name, then we call that function using the rig in the sequencer we added
- [x] Remove selection range in forward control rig tool
	- FK bake button (in "normal picker")
	- Button to open the delete picker
	- Remove body 
	- Remove face (mouth delete)
	- Remove hands
	- Remove fingers
	- Select current frame for these
- [x] Foot slide
- [x] Auto focus when touching stuff in picker


- [x] Turning off sequencer and starting it back up gets rid of the bone issue (or is it that a transaction not ended)
- [ ] Curve sequencer heeft tools zoals mocap editing tools om curves minder noise te geven etc. <span class="blue">Zet dit in documentatie</span>

- [x] Willen we baked of kan het toch nog live?

- [x] Decoupled session sequencer from midi

- Post processing pipeline in unreal engine character creator fixes some eye related baking, so i changed my implementation to only alter the eye data in the post processing pipeline
	- [ ] Get CC post processing blueprint changes into my git
	- [ ] Add these changes to Galya's and Jose's machines

Week 3 - 4 Aug
- Galya can start working on BAK a little 
- Post processing status in lifecycle file so we can rerun that part when everything is pp'ed.
- SignIO presentatie in NGT
- CV
- Lees transition papers
Verwachting gelden overzetten (7 sept  - 11 sept)

Pickers:
- [ ] Add singleassetselection to the pickers
- [ ] Auto focus

Tongue
- [ ] Key current
- [ ] Updating values based on sequencer

- [ ] New tool to check what has been post processed


- [x] Copy paste last keyframe doesnt take into account current frame
	- [x] Test changes
- [x] meeting floris
	- Vraag al iemand extra?
	- Vraag of we deadline halen
		- Willen we eerst alles opnemen en kunnen we later nog post processing afmaken?
	- [x] Volle dagen opnemen aantal keer met Jose
	- Zal ik 10 per dag post processen? <span class="blue">Laten we dat doen met oog op developen tools. Wel laten nakijken natuurlijk.</span>
	- Post processing face tool
	- Contract, info vorige keer

### Post processing work
- <span class="red">Post processing 2026-07-31</span>
		

- [x] what about gc.collectgarbageeveryframe ?

- Leak/Memory growth lijkt heel erg op alsof het van Unreal zelf is. Ik open lege sequence, add de CC avatar, add een animatie, en dan groeit het.
	- Lijkt alleen bij CC avatar te gebeuren

- JamesDev
- [ ] Test audio driven lip sync?

- [x] profiler practice
- [ ] avatar en anims meenemen naar huis voor testing

- [x] Check support ticket for headshot if it works now
	- Reimport mesh in unreal -> select import morphs and then it works
- [ ] Stylized avatar in CC? Voor signlab. Kopen?
- [x] Session sequencer does not remember anymore because we are not using asset loading but asset registry, go ahead and <span class="blue">test</span>
	- [x] On restart the status of the sessionsequencer is broken (it does not show that it has checkpoints and its pointing to an animation that is not opened). It still functions though
	- [x] On remove animation and re-add animation, the session sequencer queue does not show whether it has chedckpoint or is already baked? If I want to load those however it does show that it knows. So its only the initial loading that is failing i guess. After loading them it does show in the queue. So we will need to fix that so it shows it already from initial load.

### Demo render
- [ ] Cloth and hair physiics for demo?
- [ ] Scene
- [ ] Use mocapped camera