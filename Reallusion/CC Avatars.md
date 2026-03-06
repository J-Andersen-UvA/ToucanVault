#Reallusion 

## Twistbones
^7e9cc1
The twistbone is triggered through the post process blueprint, it reacts to the handbone rotating.
After further research, the twistbone isnt used anywhere. BUT, its most likely there because the post process blueprint is using copy from source mesh. So its likely that it expects copy from MH, which means it MH will drive the twistbones, meaning that if we want Vicon -> CC with twistbones that we will need to look into MH twistbone blueprint and copy paste that over.

## Rig
Reallusion has made a complex rig for the Character Creator avatars to be used in <span class="blue">Unreal Engine</span>. The rig has the standard controls as we know, an ability to switch between FK and IK for the hands and feet, a face rig, and a rig picker ui tool.

**Sequencer**
Getting the rig working layered in the sequencer requires that you turn off the post processing blueprint on the skeletalmesh.
![[Pasted image 20260219133729.png|500]]

**Picker**
The picker gives us the ability to quickly select controls.
![[Pasted image 20260219130536.png|400]]

## Adjusting colors in character creator
Don't use diffuse, it will only work for Unreal and CC. Importing into Blender, we see that it fails. So we will need to <span class="blue">adjust the colors of the base color texture in CC.</span>
