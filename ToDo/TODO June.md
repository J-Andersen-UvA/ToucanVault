- Weken voor vakantie proberen meer op te nemen zodat Jose kan post processen idpv opnemen

<u>06/01</u>
- JamesDev
- Nieuwe avatar in Babylonjs
- Blendshapes in Babylonjs
- Achtergrond kleur

<u>06/02</u>
Betere graphics babylonjs?
- [x] Background color picker
- [x] Sharper rendering
- [x] Lighting
- [x] Playbar added back in

<u>06/03 - 06/05</u>
- [x] Floris meeting
	- Al wat werk gedaan om babylonjs er beter uit te laten zien.
	- Misschien kan Mark nog eens kijken naar de textures (of ik), want die worden ook hard aangepakt momenteel
- [x] Dovenschool bezoek
- [x] Moet ik aansluiten bij Dutch Signs?
- [x] Mail James planning vraag (en vakantie)
- [x] Idle animation met kijken in de camera (default positie van camera)
- [x] Textures minder comprimeren
- [x] Gomer bericht sturen met changes van mijn babylonCC repo
- [x] Checkpointing in PP

<u>06/08</u>
- [x] Jos inleiden
- [x] James Dev

<u>06/09 - 06/10</u>
- [x] Digits conversion fout?
	- Lag aan import in blender. Nu zijn de wenkbrouwen ook blend idpv opaque
- [x] Signing avatar3
- [x] Digits and Mitt idle
- [x] Start on viseme picker

<u>06/11</u>
- [x] Rekey -> copy paste last keyframes for all (including zeroes)

<u>06/12</u>
- [x] Record all oral face components with Jose (did it on my own)
- [x] Recordings with Jose
- [x] Jos
- [x] Contact Tobias

<u>06/15</u>
- [x] Record mouthings
- [x] Mouthing priorities
- [x] Update Tongue picker values same way we do the mouthing
- [x] teeth controls
- [x] Test copy paste last keyframe in pipeline
- [x] SMEAR avatars
- [x] Automatically pick/refresh body rig in picker

<u>06/16</u> 
- [x] JamesDev
- [x] Bake & Save To, button. In session sequencer
- [x] Open mouthing window button in picker
- [x] Open mouthing window and then to next sequence breaks rig controls in viewport?
	- garbage collect when closing window fixes it when we close the window
	- Not evaluating the rig through getlocalcontrolrigfloat helps. So we only do this when time changed. Made a new helper to get that done.
- [x] Fix buttons, collar and sleeves of Palmer

<u>06/17</u>
- [x] Collect pictures for James
- [x] More avatars JamesDev
- [ ] Mitt, give face blends
	- There are some more issues with Mitt. For some reason im not able to put digits skeleton on her. Am I even using the correct version of Digits?
- [x] Setup part done in JamesDev, now we need to actually step through the experiment

<u>06/18</u>
- [x] Check out Unreal 5.8
- [x] JamesDev anim game loop
- [x] In the control page, inject the story with current step
- [ ] Pages should have return to main and the extra buttons
- [ ] Logging info JamesDev

<u>06/19</u>
- [ ] Opnames
*Meeting*
- [ ] Nieuwe paper idee? Face post processing vergelijken met niet, en met niks aan gezichtsexpresies
- [ ] Contract?
- [ ] Headshot avatar potential en issues
### PP-Pipeline
- [x] Fix fetching of rig in body picker (make it like the face picker)
- [x] Safe current sequence (checkpointing)
- [x] Bug oplossen als volgende anim todo dat de <span class="red">!</span> niet werkt.
- [ ] keyboard short-cuts voor picker functionaliteiten?
- [ ] Pose lib
	- Use non-layered rig?
- [ ] Update Plugins in Galya and Jose PP
	- [ ] PalmerPolo
	- [ ] SessionSequencer
- [ ] Laggy on certain animations?

- [ ] Viseme
- [ ] Test audio driven lip sync?
### Demo render
- [ ] Cloth and hair physiics for demo?
- [ ] Scene
- [ ] Use mocapped camera