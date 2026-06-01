<u>13/5/2026</u>
- [x] Ask Floris about time management and James project

<u>18/05 - 19/05</u>
- [x] Fix replay anim to not leak (moved to animbp, still leaks but way less. Reported bug by unreal engine about looping animations.)
- [x] Fix Polo Color and mesh hide in pants

<u>21/05 - 22/05</u>
- [ ] Recording session zero
	- [x] Camera encoding okay?
	- [x] Make nice retarget
	- [x] Test data in Unreal PostProcessing pipeline
		- [ ] Ask gomer to make a fetch blackmagic video button on PPWebsite
		- [x] Implement loading of PPVideo
- [x] Digits hair
- [x] Docu compile

<u>26/05</u>
- [x] PalmerPolo in recording pipeline?
	- The issue of getting him to work in the old pipeline is that it needed its <span class="blue">skeleton assigned in the post processing blueprint</span>
	- As for the replayActor, the issue was that the materials werent properly assigend (prob a bug in Unreal when you switch skelmesh). I solved it simply by adding a new replayActor to the scene and using that one.
- [x] PalmerPolo in post processing pipeline?
	Doesnt really take anything to get it to work thanks to the modular code :)
	- Add PalmerPolo to project
	- In sessionSequencer Configuration set PalmerPolo
- [x] Implement loading of PPVideo
	- [x] Align anim to timecode
	- [x] Button to load video and align to timecode
	- [x] Configuration path to set video location (fuzzy match auto load)

<u>27/05</u>
- Tongue control in PP
	- [x] Setup EUW
	- [x] Tongue XY EUW

<u>28/05 - 29/05</u>
- [ ] Update Plugins in Galya and Jose PP
	- [ ] PalmerPolo
- [x] Fix lighting of Blackmagic camera
- [ ] Test audio driven lip sync?
- [ ] JamesDev?
- [x] Tongue Control
- Weken voor vakantie proberen meer op te nemen zodat Jose kan post processen idpv opnemen

<u>01/06</u>
- [ ] Fix fetching of rig in body picker (make it like the face picker)
### Recording pipeline / Bak prep
- [x] Check for memory issues Unreal Engine, how long can we record without having to restart <span class="blue">Much less of an issue as per tests on 22 may</span>
- [x] CSV recording location bug
- [x] Test camera video re-coding pipeline.
- [x] Recalibrate cameras
- [x] Test Pipeline, with new camera
- [x] Check video recording where timecode lives
- [x] Finish Digits
	- [x] Hair
- [x] Implement new camera into Pineapple pipeline
	- [x] Service in pineapplediscovery
	- [x] Service with zeroconf in blackmagic_control github
	- [x] bat file for quick launch
	- [x] Check if we can use signcollect for start and stop record now
- [x] Move old cameras back for whole body rec
- [x] Optimale retarget naar Jose
### Documentation
- [x]  Compile repos
	- [x] Order based on functionality
	- [x] Write single sentence for each repo to explain what it is
	- [x] Add links to git of course
- [x] Timecodes in recording docu
- [x] Blackmagic camera in recording docu
### Post processing pipeline
- [ ] [[Picker & rig]]
	- [ ] Pose lib
- [ ] Bug oplossen als volgende anim todo dat de <span class="red">!</span> niet werkt.
- [x] <span class="red">CSV Writer schrijft naar verkeerde loca, alleen de base name, ook de metadata</span>
- [ ] Toevoegen van video data gesynced achter Unreal Rig?
- [ ] Twistbones using rbf?
- [x] Idpv next animation button, moet het next unprocessed button zijn
- [x] Bake and save has to also save (make package not dirty)
- [x] Bug send by galya?
- [ ] short-cuts voor picker functionaliteiten?
- [ ] rekey mss beter als copy paste prev key knop?
### Demo render
- [ ] Cloth and hair physiics for demo?
- [ ] Scene
- [ ] Use mocapped camera
### etc
- [ ] Sommige animaties nog met verkeerde avatar op post processing website. Voorbeeld:
	2134, gebruikt RPM maar is er wel als CC (want ik heb lokaal gechecked en het is present).
- [ ] Nog nieuwe drive nodig?
- [ ] Ask mark to embed timecodes in glb and blendshapes (email him)
- [x] Send avatar and tool to anders
- [x] Send request about tool to mark <span class="red">Instead i added a script that makes the sidecar out of fbx instead of csv</span>
- [x] Paper / git (A Scalable Data Pipeline for ASL Media Processing and Annotation)
