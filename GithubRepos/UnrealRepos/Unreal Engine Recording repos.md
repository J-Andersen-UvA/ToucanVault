All Github repositories I have created that are relevant to our recording process. From recording to controlling avatar animations.

## TakeRecorderUE
[J-Andersen-UvA/TakeRecorderUE](https://github.com/J-Andersen-UvA/TakeRecorderUE)
TakeRecorder hook for SignCollect recording website. You can change the socket endpoint. In Unreal, under the ToucanTools tab, click "Run Take Recorder" to start the main loop of the script.
![[Screenshot 2026-05-21 135022.png]]
The config.yaml defines which Actor to record on and on what actor to replay the animation data.
As for replaying we rely on Unreal Engine functionalities. Inside the Actor Blueprint define a current anim, and inside the anim blueprint do the following:
![[Screenshot 2026-05-21 135101 2.png|700]]![[Screenshot 2026-05-21 135107.png]]

---

## MocapStreamManager
[J-Andersen-UvA/MocapStreamManager: A mocap stream manager for avatar animation in Unreal Engine. Sync face and body streams from Live Link onto an avatar with timecodes.](https://github.com/J-Andersen-UvA/MocapStreamManager)
Setting up each of our mocap streams (vicon and llf) can be bothersome. Especially with timecodes. This Manager helps bring each of the separate functionalities under one roof. Go through each "Relevant Window" from left to right to find each functionality that needs to be linked. Click "Refresh" so the window can fetch changes. Assign the body and face anim streams through the window instead of having to manually set it for each avatar.
![[mocapManager.png|400]]

--- 

## ARKitCurveMapper
[J-Andersen-UvA/ARKitCurveMapper](https://github.com/J-Andersen-UvA/ARKitCurveMapper)
Purpose of this unreal plugin is to make it easier to map ARKit values from live link face onto any avatar. Usually avatar creators provide the mapping, but it often doesn't work for whatever reason. So this approach should make it a bit easier.

---

## LiveLinkFaceCSVWriter
[J-Andersen-UvA/LiveLinkFaceCSVWriter](https://github.com/J-Andersen-UvA/LiveLinkFaceCSVWriter)
The classic way of getting a LLF recording in csv format is by recording directly on the phone. This library writes the stream that comes into unreal engine directly to a csv, so no more need of recording directly on the phone (and no more osc communication between the phone and whatever).

---

## LiveLinkMultiIPhone
[J-Andersen-UvA/LiveLinkMultiIPhone](https://github.com/J-Andersen-UvA/LiveLinkMultiIPhone)
Record using multiple IPhones, write to a single CSV, animate a single avatar using more sources.

