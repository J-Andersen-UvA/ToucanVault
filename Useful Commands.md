List file tree:
```bash
tree /f
tree /f > tree.txt
```

Sym Link (Command Prompt as Administrator):
```shell
# folder <linkName> <originalFolder>
mklink /D "C:\Path\To\LinkName" "C:\Path\To\TargetFolder"
# file <linkName> <originalFile>
mklink "C:\Path\To\LinkName.txt" "C:\Path\To\TargetFile.txt"
```
*After changing a name, you will need to do this again. You cannot change a symlink*


Touch in windows:
```bash
type nul > README.md
```

Auto setup plugin in Unreal Engine:
```bash
init-plugin.ps1
```
That script init-plugin.ps1 is added to the environment variable PATH.
Run it in the root folder of the plugin, it uses the name of that folder.
Here is the actual command: [[Auto make plugin folder]]
 