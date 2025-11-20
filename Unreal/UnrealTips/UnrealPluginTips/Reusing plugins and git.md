We can make a plugin a symbolic link in windows 10 and 11. Then we can reuse it like that in various projects whilst having only one repository:
```bash
mklink /D "C:\Users\VICON\Documents\Unreal Projects\UE5_7_preview\Plugins\BlendshapeTools" "C:\Users\VICON\Desktop\Code\BlendshapeTools"
```

Or we fork/clone a repo, depends on what you want.