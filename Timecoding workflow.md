To timecode we use a tentacle sync E that jam syncs the Vicon Lock.

## Vicon
To set that up read [[Genlocking - Timecoding - Vicon]].

## iPhone
The iPhone can read from the same tentacle sync E:
1. Go to Settings in LLF
2. Timecode
3. Set it to the Tentacle Sync that is used by the Lock
If you cannot find it, make sure to detect it first in the Tentacle app in the iPhone.

## Unreal Engine
We don't read directly from the tentacle sync in Unreal Engine, instead we define the Vicon stream as the Timecode Provider.
To accomplish this we need to set up a few things:
1. Enable the timed data monitor plugin
2. Add the live link sources (usually ARKit, Vicon, and a camera if you want)
3. Set the evaluation modes to Timecode
4. Reuse or make a new Blueprint class: timecodeprovider
	1. Inside the blueprint set the subject key to use the Vicon Live Link source
5. Use the shortcut to provider settings button to go to the Project Settings
	1. Under Timecode set the Timecode provider to the blueprint
6. Hit the calibrate button, observe the upper right of the Timed Data Monitor, if its green its synchronized
![[TimedDataMonitor.png]]
