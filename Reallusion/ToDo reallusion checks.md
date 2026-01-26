- [x] What does the import-export pipeline look like [[Importing RL_Plugin - importing avatars into unreal]]
	- [x] CC -> iClone -> UE <span class="blue">Works</span>
	- [x] CC -> UE5.5 (auto plugin) Doesnt work, but im waiting for response through: [Live Link Transfer or FBX Drag-In Crash Issue - Pipeline / Unreal Engine - Reallusion Forum | Community for iClone, Character Creator & Cartoon Animator](https://discussions.reallusion.com/t/live-link-transfer-or-fbx-drag-in-crash-issue/15796/3)
- [ ] How well does it work in the vicon pipeline
	- [x] Vicon -> UE
	Nothing to complain about, as soon as i have it imported in unreal engine it functions the same as the RPM.
	- [x] Blendshapes
	For the blendshapes I made a tool to make it easier to use: [J-Andersen-UvA/ARKitCurveMapper](https://github.com/J-Andersen-UvA/ARKitCurveMapper)
	Because we save the original csv of the iPhone, we can use the map created with the ARKitCurveMapper. If we want to retarget directly from RPM glassesGuy blendshape names, we can make a new map with the curvemapper and use the animation blueprint to read out the original values from the animation.
	- [x] Recording motions through pypipeline
	It works just fine as soon as we change all the values to the new avatar. Only the <span class="blue">forward</span> has changed, so we might need to add that to the export settings so we don't accidentally export into the wrong direction.
	- How well it works with the export is explained in the babylonjs part
- [ ] How well does it work in babylonjs
	Blendshapes work as long as you get the fbx and then take it through the <span class="blue">npm</span> converter.
	Getting hair working is a lot harder.
- [ ] How do the cartoon characters look
- [ ] How clean of a retarget can we make between RPM and CC
- [ ] How much is the total cost?
- [ ] Cartoony avatar?

