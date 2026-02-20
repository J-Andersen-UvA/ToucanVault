#HSL #Blade #ShogunPost

Finally a categorized list:
[Commands by category - Shogun Post 1.15 documentation - Vicon Help](https://help.vicon.com/space/ShogunPost115/276207757/Commands+by+category)

**Find folder and replace:**
```hsl
string $cur = `GetPathToExportTo`;
string $path = "";
int $index;

$index = `strReverseFind $cur "/"`;
$path  = `strLeft $cur $index`;

print $path;
$path = `strReplace $path "shogun_live" "shogun_post"` + "/";
print $path;
```

```hsl
// Prepare export
setParameter "GlobalScale" 1.0 -retargeting -onMod tobias;
select "tobias\\Retargeting";
SelectChildren_Add_All;
delete;
select "Solving" -a;

// Get shogun post path
string $cur = `GetPathToExportTo`;
string $path = "";
int $index;
$index = `strReverseFind $cur "/"`;
$path  = `strLeft $cur $index`;
$path = `strReplace $path "shogun_live" "shogun_post"` + "/";

// Add file name and export
string $fileName = "";
string $fileNameExtension = `GetPathToExportTo` + ".mcp";
$fileName = `getFileTitle $fileNameExtension`;
$path = $path + $fileName + ".fbx";
SelectChildren_Add_All;
saveFile -s $path;
```