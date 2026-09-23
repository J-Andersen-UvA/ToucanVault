- [x] Fix leaks in sequencer Abstraction
- [x] Make Rig usage faster in Picker
- [x] Make recording pipeline faster
- [x] Check Leaks in recording
- [x] Test recording pipeline once more
- [x] Splay slider additive with offset instead of set
- [ ] Audio driven lip sync
- [ ] Papers lezen
	- Papers over hamnosys
	- Papers over sign language animation generation
	- Over Transitions
	- Over retargeting
- [x] Have to click replay actor and open details panel once during a recording session otherwise leaking???
	- Its the take recorder panel, as soon as any source is added to it it starts climbing in the object count. Then if i switch to another tab it stops, and it grows again if i return...
- [x] Update splay slider based on values in sequencer
	- Get the splay value by inversing one of the splay degrees.


- [ ] Na locatie files, locale disk opschonen
- [ ] Should we create a pass that repairs hand positioning, hand shape, maybe even face, on any avatar that has these areas defined? Like a specialized retarget for sign language?
- [ ] Number recognition example for ai practice
- [ ] Zero is very slow in picker tool

- [ ] Volgens mij moet ik nog een account naam krijgen zodat ik signcollect kan mounten
- [ ] ViconDashboard mist nog de blackmagic files locatie
- [ ] Lijkt ook alsof er meerdere locaties zijn waar er backups zijn van de animaties? Want ik had al een mount van SignCollect voor blackmagic files, en daar zie ik mocap files tot 2026-01-29
- [ ] Mss ook goed als ik een compilatie kan krijgen van je codebases?
ls -la /mnt/bigstorage/fbx
ls -la /web/gebarenoverleg_media/studioFiles/mocapFiles


automatisch genereren, automatische post processing


- [x] CV
- [x] Paper alinea
- [x] Rig selection method, change it to the faster method like in the forward picker
- [x] Speed up the picker!
- [ ] Get rid of throat wrinkles
- [x] Checkpoint en next todo swappen van kant
- [x] says editing when not actuyally editing on load
- [ ] Curve sequencer heeft tools zoals mocap editing tools om curves minder noise te geven etc. <span class="blue">Zet dit in documentatie</span>
- [ ] Auto focus for all tools
	- Splay
	- What else needs it still?
- [ ] New tool to check what has been post processed
- [ ] avatar en anims meenemen naar huis voor testing
- [ ] Stylized avatar in CC? Voor signlab. Kopen?
- [ ] Ability to save session changes? E.g. keep eyebrows raised across multiple animations

- Post processing pipeline in unreal engine character creator fixes some eye related baking, so i changed my implementation to only alter the eye data in the post processing pipeline
	- [ ] Get CC post processing blueprint changes into my git
	- [ ] Add these changes to Galya's and Jose's machines

Pose library
- [ ] [[PosePasting]]
- [x] Leaking?
- [x] Add figure about rig base to the readme

FK selection rig:
- [ ] shift clicking not working for single frame selection method


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