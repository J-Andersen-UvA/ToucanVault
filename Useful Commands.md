List file tree:
```bash
tree /f
tree /f > tree.txt
```

Sym Link (Command Prompt as Administrator):
```shell
# folder
mklink /D "C:\Path\To\LinkName" "C:\Path\To\TargetFolder"
# file
mklink "C:\Path\To\LinkName.txt" "C:\Path\To\TargetFile.txt"
```
