### Context aware retargeting
- [ ] Should we create a pass that repairs hand positioning, hand shape, maybe even face, on any avatar that has these areas defined? Like a specialized retarget for sign language?
### Data
- [ ] Moeten we nog die vvids bewaren of niet
- [ ] home/gomer/viconsync waarom niet auto remove.
- [ ] Hoe publishen op figshare script checken.
- [ ] avatar en anims meenemen naar huis voor testing
### Avatar
- [ ] Fix mesh elements on palmer: sleeve and button
- [ ] Get rid of throat wrinkles
- [ ] Stylized avatar in CC? Voor signlab. Kopen?
### PP Pipeline
_Body hands:_
- [ ] Pose Pasting kleine paper? 
- [ ] Curve sequencer heeft tools zoals mocap editing tools om curves minder noise te geven etc. <span class="blue">Zet dit in documentatie</span>
- Post processing pipeline in unreal engine character creator fixes some eye related baking, so i changed my implementation to only alter the eye data in the post processing pipeline
	- [ ] Get CC post processing blueprint changes into my git
	- [ ] Add these changes to Galya's and Jose's machines
- [ ] Show Body control button not always working
- [ ] New tool to check what has been post processed

_FK selection rig:_
- [ ] shift clicking not working for single frame selection method

_Face:_
- [ ] Focus not working
- [ ] Slider changes to aggresive for the ctrlz
- [ ] Not live updating anymore
#### JamesDev
- [ ] Test audio driven lip sync?
### Demo render
- [ ] Cloth and hair physiics for demo?
- [ ] Scene
- [ ] Use mocapped camera