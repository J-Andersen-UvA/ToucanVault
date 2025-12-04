#UnrealEngine #TroubleShooting 
**Also see the following file for more explanation:** [[Sequencer unreal frame rates]]

Unreal engine uses the following for levelsequences:
- tickrate
- displayrate
- framerate
The important part is that you understand the following: https://youtu.be/OSwqooOwTls?si=Gfy-mUhPe77x3jWx&t=425

Here is more documentation on it: [Changing Sequencer Section End Range in C++ - Development / Cinematics & Media - Epic Developer Community Forums](https://forums.unrealengine.com/t/changing-sequencer-section-end-range-in-c/472819/4)

Later on when baking I got:
```log
Incompatible frame rate provided: 24 fps not a multiple or factor of 30 fps
```
To solve it I had to set the default framerate of the PROJECT to 24.
```cpp
UAnimationSettings* AnimSettings = UAnimationSettings::Get();
const FFrameRate SeqRate = MovieScene->GetDisplayRate();
AnimSettings->Modify();
AnimSettings->DefaultFrameRate = SeqRate;
```
