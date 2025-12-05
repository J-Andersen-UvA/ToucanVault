#Blendshapes #UnrealEngine #UnrealPython 

1. curve names in skeleton
2. morph target names in skeletalmesh

### 1 Curve names in skeleton
Add the curve names you want in the skeleton curves section (you can copy paste it over from other avatars).

### 2 Morph target names in skeletalmesh
Use a script to rename the original morphs, this only works when the editing tool is <span class="blue">DISABLED</span>.
Here is the script I used:
```python
import unreal

OLD_PREFIX = "Debra"
NEW_PREFIX = "glassesGuy"

def rename_morph_targets():
    selection = unreal.EditorUtilityLibrary.get_selected_assets()
    mesh = next((a for a in selection if isinstance(a, unreal.SkeletalMesh)), None)
    if not mesh:
        unreal.log_error("Select a SkeletalMesh.")
        return
  
    morph_targets = mesh.get_editor_property("morph_targets")
    # Create a mapping of old names to new names
    rename_map = {}
    for mt in morph_targets:
        old_name = mt.get_name()
        if old_name.startswith(OLD_PREFIX):
            new_name = old_name.replace(OLD_PREFIX, NEW_PREFIX, 1)
            rename_map[old_name] = new_name
  
    if not rename_map:
        unreal.log_warning("No morph targets found with prefix: " + OLD_PREFIX)
        return
  
    with unreal.ScopedEditorTransaction("Rename morph targets"):
        # Mark the mesh as modified
        mesh.modify()
        for old_name, new_name in rename_map.items():
            try:
                # Access the morph target and rename it using the rename method
                for mt in morph_targets:
                    if mt.get_name() == old_name:
                        # Mark the morph target as modified before renaming
                        mt.modify()
                        # Use the rename method directly on the morph target
                        mt.rename(new_name)
                        unreal.log(f"Renamed: {old_name} -> {new_name}")
                        break
            except Exception as e:
                unreal.log_warning(f"Error renaming {old_name}: {str(e)}")
        # Rebuild the morph targets array to apply changes
        morph_targets = mesh.get_editor_property("morph_targets")
        mesh.set_editor_property("morph_targets", morph_targets)

    # Force the mesh to rebuild its morph target lookup table
    try:
        # This will rebuild the mesh with the new morph target names
        unreal.EditorAssetLibrary.save_asset(mesh.get_path_name())
        unreal.log("Morph targets renamed and saved successfully.")
    except Exception as e:
        unreal.log_warning(f"Error saving mesh: {str(e)}")

rename_morph_targets()
```
