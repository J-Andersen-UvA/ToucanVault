#purpleMaterials 
**Issue timeline, for reallusion hair**

**Issue**
Hair coming from CC/Unreal via fbx -> glb (npm converter) looked wrong, purple black. because the hair material didn’t survive conversion correctly (alpha/opacity + texture routing).

**Fix**
Exporting the avatar through **Blender to GLB** preserved the correct hair-card material.
The hair textures rely on **baseColor alpha** (opacity in the albedo’s alpha channel). Once Blender exported the GLB, Babylon could use that correctly.

**Issue**
I could see the scalp reflectively through the hair.
![[Pasted image 20260127142546.png|400]]

**Fix**
put the scalp alpha index lower than the hair alpha index.

**Issue**
Faintly, I can see the silhouette of the scalp through the hair. 
![[Pasted image 20260127142634.png|400]]

**Fix**
ChatGpt suggest using alpha test instead of Alpha blend, but it looks better with blend imo. To still make the headline disappear, I had to turn on the backface culling for the hair.

**Issue**
The mustache and beard are shining?

**Fix**
Up the roughness (0,6).
