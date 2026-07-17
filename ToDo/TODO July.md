- [x] Check mocap setup for Debby
- [x] Meeting Anna
- [x] Verse?
- [x] session sequencer now bakes timecodes
- [x] New router?
- [x] Test if timecodes are exporting in main pipeline.
	- We had to save first in order to get the export to work. Such a stupid thing that we are forced to do. Why can we even export an unfinished asset???
- [x] Renders maken voor Rob/Jart.
- [ ] Viseme
	- [ ] Add tongue and Jaw control to the viseme sliders.
	- [ ] Reset the controls for the jaw and tongue if nothing is selected (it stays stale from previous change, so maybe just make sure it always sets to 0 first and then apply changes?)
	- [ ] Add jaw controls so we can combine the manual with the automatic ones 
- [ ] Copy paste last keyframe doesnt take into account current frame

- [ ] what about gc.collectgarbageeveryframe ?

- JamesDev
- [ ] Test audio driven lip sync?

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