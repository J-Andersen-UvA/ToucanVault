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

Count unique folders minus the last part:
```shell
# Get all subfolder names
$folders = Get-ChildItem -Directory | Select-Object -ExpandProperty Name

# Strip the final underscore + digits, get unique list, then count
$uniqueCount = ($folders | ForEach-Object {
    $_ -replace "_\d+$",""
} | Sort-Object -Unique).Count

$uniqueCount
```

Smaller images in obsidian:
use `|` and then the size
```
![[imagelocation|400]]
```
