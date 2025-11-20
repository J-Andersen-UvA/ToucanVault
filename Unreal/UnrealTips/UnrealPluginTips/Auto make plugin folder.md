#UnrealEngine 
```bash
# Get the current folder name
$pluginName = Split-Path -Leaf (Get-Location)

# Define paths
$pluginFile = "$pluginName.uplugin"
$sourceDir = "Source\$pluginName"
$publicDir = "$sourceDir\Public"
$privateDir = "$sourceDir\Private"
$buildFile = "$sourceDir\$pluginName.Build.cs"
$cppFile = "$privateDir\${pluginName}EditorModule.cpp"

# Create folders
New-Item -ItemType Directory -Force -Path $publicDir | Out-Null
New-Item -ItemType Directory -Force -Path $privateDir | Out-Null

# Create files if they don't exist
if (-not (Test-Path $pluginFile)) {
    @"
{
    "FileVersion": 3,
    "Version": 1,
    "VersionName": "1.0",
    "FriendlyName": "$pluginName",
    "Description": "$pluginName plugin",
    "Category": "Custom",
    "Modules": [
        {
            "Name": "$pluginName",
            "Type": "Editor"
        }
    ]
}
"@ | Out-File $pluginFile -Encoding utf8
}

if (-not (Test-Path $buildFile)) {
    @"
using UnrealBuildTool;

public class $pluginName : ModuleRules
{
    public $pluginName(ReadOnlyTargetRules Target) : base(Target)
    {
        PCHUsage = PCHUsageMode.UseExplicitOrSharedPCHs;
        PublicDependencyModuleNames.AddRange(new string[] { "Core", "CoreUObject", "Engine", "Slate", "SlateCore" });
        PrivateDependencyModuleNames.AddRange(new string[] { "UnrealEd" });
    }
}
"@ | Out-File $buildFile -Encoding utf8
}

if (-not (Test-Path $cppFile)) {
    @"
#include "$pluginName.h"
#include "Modules/ModuleManager.h"

IMPLEMENT_MODULE(FDefaultModuleImpl, $pluginName)
"@ | Out-File $cppFile -Encoding utf8
}

Write-Host "✅ Plugin structure initialized for $pluginName"
```
