### Why morph target renaming doesn’t work inside Unreal Engine through script yet

Even though there is a: <span class="blue">bool RenameMorphTarget (FName InOldName, FName InNewName)</span> in Engine/SkeletalMesh.h, it does not seem to be working. I got as far as renaming the names we can see visually in the skeletalmesh editor, and automatically changing the names in the skeleton curves (which is needed I will explain in a second). But still it did not work. 



### Bulk Renaming Morph Targets in UE5

Hi all, 

I’ve been digging into **bulk renaming morph targets inside Unreal Engine 5.7** (also had attempts in 5.5 and 5.6) and wanted to share findings, since I hit a wall.

### What I tried

I wrote a small editor plugin that:
1. Iterates over `USkeletalMesh->GetMorphTargets()`
2. Attempts to rename each morph to match a new naming scheme
3. Updates skeleton curves to match

Example snippet (simplified):
```cpp
for (UMorphTarget* Morph : SkelMesh->GetMorphTargets())
{
    const FString OldName = Morph->GetName();
    const FString NewName = OldName.Replace(TEXT("UniversityStudent"), TEXT("glassesGuy"));

    Morph->Rename(*NewName, nullptr);  // Attempt rename
    SkelMesh->RegisterMorphTarget(Morph); // Re-register
}
```
### What happened
- Unreal would **show a dialog** listing renamed morphs ✅
- Skeleton curves updated ✅
- But after saving, the **.uasset on disk still had the old names** ❌
- On reload, Unreal reverted everything ❌

I know that USkeletalMesh::RenameMorphTarget exists, I have attempted using it but got just as far.

Please let me know if you have any ideas!