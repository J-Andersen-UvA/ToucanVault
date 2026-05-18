<u>Reminder notes:</u>
Prio post processing
- BAK
- ZinInNGT
- HH

<u>13/5/2026</u>
- [x] Ask Floris about time management and James project

<u>18/05/2026</u>
- [ ] Fix replay anim to not leak
### Recording pipeline / Bak prep
- [ ] Check for memory issues Unreal Engine, how long can we record without having to restart
- [x] CSV recording location bug
- [x] Test camera video re-coding pipeline.
- [x] Recalibrate cameras
- [x] Test Pipeline, with new camera
- [x] Check video recording where timecode lives
- [ ] Finish Digits
	- [ ] Hair
- [x] Implement new camera into Pineapple pipeline
	- [x] Service in pineapplediscovery
	- [x] Service with zeroconf in blackmagic_control github
	- [x] bat file for quick launch
	- [x] Check if we can use signcollect for start and stop record now
- [x] Move old cameras back for whole body rec
- [ ] Optimale retarget naar Jose
### Documentation
- [ ]  Compile repos
	- [ ] Order based on functionality
	- [ ] Write single sentence for each repo to explain what it is
	- [ ] Add links to git of course
- [x] Timecodes in recording docu
- [x] Blackmagic camera in recording docu
### Post processing pipeline
- [ ] [[Picker & rig]]
	- [ ] Pose lib
- [ ] Bug oplossen als volgende anim todo dat de <span class="red">!</span> niet werkt.
- [ ] <span class="red">CSV Writer schrijft naar verkeerde loca, alleen de base name, ook de metadata</span>
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
