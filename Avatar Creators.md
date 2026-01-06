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

It takes some getting used to the Character Creator 5, but its basically a big asset store. Makes me think of the Sims. Head hair and facial hair looks good in BabylonJS.

The blendshapes are very detailed on the realistic avatars. Especially the CC5 blendshapes. But they don't have the exact names from the ARKit, but the ARKit blendshapes are all present, so we could remap. The CC4 Extended blendshapes are more similar to the ARKit blendshapes, naming wise and visually.

---

**fortnite character**
Currently UEFN does not have an avatar creator

---

**MeshyAI**

---

**hunyuan3d**

---
