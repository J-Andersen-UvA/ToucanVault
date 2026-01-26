- [x] What does the import-export pipeline look like [[Importing RL_Plugin - importing avatars into unreal]]
	- [x] CC -> iClone -> UE <span class="blue">Works</span>
	- [x] CC -> UE5.5 (auto plugin) <span class="blue">Doesnt work</span>
- [ ] How well does it work in the vicon pipeline
	Nothing to complain about, as soon as i have it imported in unreal engine it functions the same as the RPM. For the blendshapes I made a tool to make it easier to use: [J-Andersen-UvA/ARKitCurveMapper](https://github.com/J-Andersen-UvA/ARKitCurveMapper)
	Because we save the original csv of the iPhone, we can use the map created with the ARKitCurveMapper. If we want to retarget directly from RPM glassesGuy blendshape names, we can make a new map with the curvemapper and use the animation blueprint to read out the original values from the animation
- [ ] How well does it work in babylonjs
- [ ] How do the cartoon characters look
- [ ] How clean of a retarget can we make between RPM and CC
- [ ] How much is the total cost?
