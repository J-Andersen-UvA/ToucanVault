- [x] Jos paper
	- [x] Wat is er aan feedback op mijn sectie, en wat is er aangepast?
	- [x] Opmerking Pagina 4
	- [x] Wat zeggen over functie?

- [ ] Tentacles sync
	- [x] Vicon
	- [ ] Unreal?
		- [ ] How's the data captured in Unreal, can we read it in after export and even as glb?
	- [x] iPhone

- [ ] Save Recorded Assets Unreal, test with disabled for cache
- [ ] Check sync tentacles met anims van unreal? Kunnen we nu csv en fbx makkelijk joinen?
	- [ ] Record timecode has to be on in the take-recorder

- [ ] [[Picker & rig]]

- [ ] Meeting floris
	- [x] Online?
	- [ ] Rig + picker voorbeeld
	- [ ] Fem avatar, haar, retargets
	- [ ] Face editing
	- [ ] Pose library

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