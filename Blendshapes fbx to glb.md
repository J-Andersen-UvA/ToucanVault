#Blendshapes 

Its a hell. But we should document it.

NPM conversion tool:
[facebookincubator/FBX2glTF: A command-line tool for the conversion of 3D model assets on the FBX file format to the glTF file format.](https://github.com/facebookincubator/FBX2glTF)
```md
- When **blend shapes** are present, you may use `--blend-shape-normals` and `--blend-shape-tangents` to include normal and tangent attributes in the glTF morph targets. They are not included by default because they rarely or never seem to be correctly present in the actual FBX source, which means the SDK must be computing them from geometry, unasked? In any case, they are beyond the control of the artist, and can yield strange crinkly behaviour. Since they also take up significant space in the output file, we made them opt-in.
```
But we still need the mesh present in the original fbx in order to do this... Which, depending on the mesh, can increase the storage used 20 fold.

