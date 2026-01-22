#Reallusion 
Download:
[Auto Setup for Unreal Engine | Free Download | Reallusion](https://www.reallusion.com/auto-setup/unreal-engine/download.html)

Video tutorial (5.7):
[Unreal Auto Setup (All-in-One) for UE 5.7 New Update | CC & UE Workflow Tutorial](https://www.youtube.com/watch?v=-o8hT175bHI)

1. Copy paste auto setup folders: plugin and content
	Auto setup folder is found in:
	`C:\Program Files\Reallusion\Shared Plugins\Auto Setup\Unreal\Auto Setup 2.0 For Unreal 5.7 (All-in-One)`
2. Go to plugin menu to confirm that the auto setup is installed
3. Drag and drop the fbx that was exported from CC using the unreal preset and the following settings:
```
1. unreal engine 5 template export from reallusion
	a. Don't embed textures
	b. Delete hidden faces
	c. Bake diffuse and specular for hair
2. Using the Reallusion Unreal Engine Auto setup plugin import FBX into Unreal
```
I had an issue with with some avatars not importing into unreal (crashing it). It was fixed by giving the avatar a beard, i will dive deaper into the issue:
![[Pasted image 20260108170654.png]]
Workaround:
Import with a beard, give the beard a transparent material.

## Potential explanations on why its failing?
- More RAM? (thats what support told me)
- Could it be that I first import an avatar with a beard, then i try another one without, then it cleans the dictionary of its values but not its keys, so therefore its missing a value for the beard key and then it points to null and therefore gets a mem error?


1. try fresh project with failing avatar, does it import? (it does not)
2. try jolene project but add beard to jolene (crash)
3. use livelink? (yesss)
4. try older version?

What do the shaders do: [Character Creator and iClone Auto Setup Plug-in Online Manual - Digital Human Setups](https://manual.reallusion.com/CC_and_IC_Auto_Setup_Plugin/ENU/CC_and_iC_Auto_Setup/1.2/02_for_Unreal/Digital-Human-Setups.htm)

### Using iClone LiveLink
1. In CC export to iClone (whilst iClone is open)
2. In iClone transfer file when the avatar is loaded and UE is open
3. It should now import into UE
![[Pasted image 20260122163526.png]]![[Pasted image 20260122163639.png]]
![[Pasted image 20260122163648.png]]
![[Pasted image 20260122163725.png]]
