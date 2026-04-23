Week 3 goals:
- Are we fully prepared for BAK?
	- [x] Move screen
	- [x] Recalibrate
	- [ ] Test Pipeline, with new camera
- Install new camera
	- [x] Timecodes on camera
	- [x] Tentacle House
	- [ ] Check video recording where timecode lives
- Headless auto retarget
	- [x] Receive anims
	- [x] Retarget anims
	- [x] Send back anims
	- [x] Deploy on github so we can use it in the server
	- [J-Andersen-UvA/AutoRetargetUnrealHeadless](https://github.com/J-Andersen-UvA/AutoRetargetUnrealHeadless)
- Upgrade to shogun live 1.19
- [Reallusion Content End User License Agreement](https://www.reallusion.com/Content/EULA/EULA.htm)
- Update documentation
- Unreal EUW for recording

Week 4 goals:
- Compile repos
- Ask mark to embed timecodes in glb and blendshapes


Setup
- [x] Move screen
	- Otherwise HH will be very difficult for the signers
- [x]  Recalibrate all cameras

- [ ] Jos paper
	- [x] Wat is er aan feedback op mijn sectie, en wat is er aangepast?
	- [x] Opmerking Pagina 4
	- [x] Wat zeggen over functie?
	- [ ] Check paper again

- [ ] Tentacles sync
	- [x] Vicon
	- [ ] Unreal?
		- [ ] How's the data captured in Unreal, can we read it in after export and even as glb?
			- I dont see it in the glb, <span class="blue">ask mark</span> to add it to the converter (keep in mind differences unreal, shogun timecodes)
		- [x] Document how its captured (on bone curves, how does it differ from fbx)
	- [x] iPhone
	- [x] Documentation on syncing and processing

- [x] Save Recorded Assets Unreal, test with disabled for cache
- [x] Check sync tentacles met anims van unreal? Kunnen we nu csv en fbx makkelijk joinen?
	- [x] Record timecode has to be on in the take-recorder
	- [x] Document about timecoding workflow [[Timecoding workflow]]

- [ ] [[Picker & rig]]
- [x] Setup machines for post processing
- [x] Introduce Jose to all the changes in the post processing pipeline

Prio post processing
- BAK
- ZinInNGT
- HH

- [x] Meeting floris
	- [x] Online?
	- [x] Rig + picker voorbeeld
	- [x] Fem avatar, haar, retargets
		- Zoek naar meer haar
	- [x] Face editing
		- Don't do it, too much effort
		- Ask actors to exaggerate their facial expressions more
	- [x] Pose library
		- Go ahead and check it out, after other priorities
	- [x] Demo
	- [x] Timecode syncing
prio:
- Fem avatar
- Auto retarget fem avatar
- New camera

- [x] Auto retarget Unreal Headless
	- [x] First with Head [[AutoRetarget]]
	- [x] Make headless version

- [ ] Drive bijna vol
	- [x] Kan ik nog harde schijf ruimte erbij?
	- [x] Genoeg slots? <span class="blue">Er is nog normale plugs voor hdd</span>
	- [ ] Stuur drive voorbeeld/request naar floris

- [ ] <span class="blue">Toevoegen van video data gesynced achter Unreal Rig?</span>
- [ ] Mocap Pipeline
	- [x] Nieuwe pipeline MET tentacles
	- [ ] pipeline documentatie rework
- [ ] Fix midi json loading
- [ ] Take recorder sequence references? (minimalize cache use)
	- [ ] Use set up sequence?
- [ ] Demo render
	- [ ] Cloth and hair physiics for demo?
	- [ ] Scene
	- [ ] Use mocapped camera
- [ ] Twistbones using rbf?
- [ ] Unreal pose library hoe additive?
- [ ] Fem avatar implement before HH [[Fem Avatar]]
	- [x] Same proportions as male avatar <span class="blue">Almost worked, still need retarget, but very minimal so only retarget is enough</span>
	- [ ] Request more hair?
- [ ] Compile all repo's in a single file
	- [ ] Order based on functionality
	- [ ] Write single sentence for each repo to explain what it is
	- [ ] Add links to git of course
- [ ] Additive Rig issue
	- [ ] is because its based on the base pose (instead of current pose)
		I suggest that we add a button "base hand" to put the hand in its base position. Then we can apply afterwards the library pose.

- Lecture on user avatar interaction and llm's 
- Assisted students on thesis