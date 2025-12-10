#var4good 
What is important to teach the students:
1. How to motion capture.
2. Animations and how to process them
3. How to implement the animations in unity.

The presentation therefore needs to be build out of these two parts.

---
## How to motion capture
[[What is motion capturing]]
- What is motion capturing?
- Why motion capture?
- How does motion capturing markers work?
	- Active - versus passivetracking, marker versus markerless
	- Retro-Reflective markers (show marker, show flash, explain infrared)
	- Infrared cameras, no location data yet
	- Triangulation for cameras during calibration
	- Marker tracking available, but no identification yet.
- How does motion capturing humans work?
	- Labelling passive markers
	- Solving into a skeleton
	- Motion capturing a face

---
## Animations and how to process them
- Skeletal animations (skeletons, meshes, weightpainting)
- Blendshapes (extremes, use cases)
- Why process animations
- Marker based post processing
- Retargeting
	- What is retargeting and why
	- retargeting in Unity explained ([[Unity retargeting]])
- Additive animation editing
	- Original method (keyframe hell)
	- Additive animation editing
	- Custom Rigs
---
## How to implement the animations in unity
- Importing avatar (normals calculate)
- Importing animations (dont forget ctrl+d)
	- Skeletal
	- Blendshapes
- Retargeting animations (select same humanoid, the anim needs to copy from avatar)
- Applying the animation onto an avatar in the scene (statemachine, animator to root object)
- Rootmotion