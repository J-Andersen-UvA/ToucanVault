#Reallusion
ReadyPlayerMe has been bought by Netflix and is closing its services from 2026. We are going to need to find a new Avatar Creator.
Previous requirements were:
- Expressive characters in the <span class="blue">body AND face</span>
- Able to run on many devices, that means also on the <span class="blue">webbrowser</span>
- <span class="blue">Masculine and feminine</span> avatars

Following are researched avatar creators and notes during my exploration

---

**AssetForge**
Meant for static meshes

---

**Reallusion - character creator 5**
Realistic avatars that also work in bablyonJS, as long as you follow a good model pipeline.

Export methods explored:
```
1. unreal engine 5 template export from reallusion
2. fbx export from unreal engine
3. convert to glb using nodejs
4. Primitive1 in babylonjs is main blendshape (wel stukke blendshape namen)
```

```
1. blender template export from reallusion
2. glb export from blender
3. Working blendshapes on all relevant meshes, and even the names are intact
```

```
1. unreal engine 5 template export from reallusion
	a. Don't embed textures
	b. Delete hidden faces
	c. Bake diffuse and specular for hair
2. Using the Reallusion Unreal Engine Auto setup plugin import FBX into Unreal

```
It takes some getting used to the Character Creator 5, but its basically a big asset store. Makes me think of the Sims. Head hair and facial hair looks good in BabylonJS.

The blendshapes are very detailed on the realistic avatars. Especially the CC5 blendshapes. But they don't have the exact names from the ARKit, but the ARKit blendshapes are all present, so we can remap. An added benefit of the extra blendshapes is that it enables us to post process the face animations much more. We should be able to get more realistic facial expression for the post processing animation, although i suspect that without a good custom rig it will take a lot of time.

There is a learning curve to using Character Creator.

Could not get all mustache movements working with the blendshapes in unreal. It works in CC, but not in UE?

---

**fortnite character**
Currently UEFN does not have an avatar creator

---

**MeshyAI**
Creates avatars using prompts.
Issues I have with AI avatars:
1. Require tokens and waiting for the server to provide the avatar, so takes a while to get them.
2. Mesh often requires rigging a skeleton and then weightpainting, etc.
3. NO blendshapes and therefore no facial expressions. I would have to do this by hand for each avatar...
4. The amount of polygons sometimes is just unusable.. ![[Pasted image 20260106145848.png|400]]
5. Control only through prompt and images.
6. No separate eye mesh, will need to create that by hand if we want eyes to be animated.
![[Pasted image 20260106152811.png|500]]![[Pasted image 20260106153108.png|500]]


---

**hunyuan3d**

---

**VRoid**
