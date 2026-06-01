- [ ] Github
- [ ] RemoveBackWall? Kitchen?

### <u>Tablet game loop</u>
We can go the remote control route:
	Run with: `-RCWebControlEnable -RCWebInterfaceEnable`
	default: `ws://127.0.0.1:30020` and to reach pc ofc `ws://<pc_ip>:30020`
Or just use build in websocket support (might be easier?)
Made a plugin that uses the build in websocket support.
Example hello world html made.



<u>Logging</u>
- Logging hand position (30times a second minimal)
- Gaze hitboxes? Head, chest, environment?

<u>Dialogue Approach</u>
- Avatar gives a question
- Player responds, wizard of oz the progression through tablet

- [ ] Tablet websocket website progression, Unreal communication
- Log speech onset offset (through tablet?) (also through audio ingame)

<u>What will change in scene</u>
- Visual distraction level
- Noise level
- What the avatar is doing


Implementation order:
- [x] Implement VR in Unreal Engine
- [ ] Implement environment + selectable conditions
	- [x] Avatars
	- [x] Start Sounds
	- [x] Test locational audio
	- [x] Items to grab
- [ ] Implement game flow / experiment setup tools
- [ ] Implement data logging
	- [ ] Working with csv
	- [ ] Stopwatch
- [ ] Implement avatars + animation pipeline
- [ ] Pilot test interaction flow and VR comfort



<u>20/05</u>
- [x] Clean up project
- [x] VR
	- [x] OpenXR template
	- [x] Grabables
- [x] Avatar state and animation machines
	- [x] Statemachine
		- [x] Animation placeholders
			- [x] Download
			- [x] Implement
- [x] Adding my favorite plugins
	- [x] ToucanCCPicker
	- [x] CC support
	- [x] Sequencer abstraction
	- [x] ARKitCurveMapper
	- [x] UnrealMidi
- [ ] CC avatar
	- [x] James
	- [x] Jari
	- [x] Palmer
- [x] Improve scene
	- [x] More performance
	- [x] Smaller scene
	- [x] Baked lighting
- [x] Debug for VR development

<u>22/05</u>
- [x] CrowdLevel

<u>26/05</u>
- [x] Patch locational audio from config



### Internet Sources
[Lip syncing in realtime from audio - Development / Programming & Scripting - Epic Developer Community Forums](https://forums.unrealengine.com/t/lip-syncing-in-realtime-from-audio/1857173/15)
