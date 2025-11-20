Directly including headers (`#include`) means hard-dependency. How can we depend on something if it is there, but ignore it if it is not present?

_plugin-to-plugin boundaries and conditional compilation_
#### 1. Add a _soft dependency_ in the `.uplugin`
example:
```md
"Plugins": [
  {
    "Name": "UnrealMidi",
    "Enabled": true,
    "Optional": true
  }
]
```
#### 2. In `.Build.cs`
example:
```cpp
PrivateDependencyModuleNames.AddRange(
    new string[] { "Projects" }
);

if (Directory.Exists(Path.Combine(ModuleDirectory, "../../UnrealMidi")))
{
    PrivateDependencyModuleNames.Add("MidiMapper");
}
```
#### 3. In C++: wrap all related code
Wrap in `#if WITH_PLUGINNAME`. Do make sure that the .build.cs contains something along the lines of:
```cpp
PublicDefinitions.Add("WITH_MIDIMAPPER=" + (bHasMidiMapper ? "1" : "0"));
```
Then in your cpp file for example:
```cpp
#if WITH_MIDIMAPPER
#include "MidiMappingManager.h"
#include "MidiMapperModule.h"
#endif
```
Or even guarding the whole implementation:
```cpp
#if WITH_MIDIMAPPER

void FToucanMidiRigBinder::RegisterRigControls()
{
    // ... full implementation here
}

void FToucanMidiRigBinder::BindRigChangeListener()
{
    // ...
}

#else

void FToucanMidiRigBinder::RegisterRigControls() {}
void FToucanMidiRigBinder::BindRigChangeListener() {}

#endif
```
