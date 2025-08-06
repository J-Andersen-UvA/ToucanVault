#UEPlugin #UnrealEngine 
1. **`.uplugin` & `.uproject` Configuration**
    
    - Create your plugin descriptor (`MyPlugin.uplugin`), declaring one or more modules (e.g. runtime vs. editor-only).

We ran into so many issues just because of the placement of the build and other files. Just make sure to fold the following general structure:
		`
		MyPlugin/                         # Root of your plugin
		├── MyPlugin.uplugin              # Plugin descriptor
		└── Source/
		    ├── MyPlugin/                 # Runtime module
		    │   ├── Public/               # Exposed headers
		    │   │   └── MyPluginComponent.h
		    │   └── Private/              # Implementation files
		    │   │   └── MyPluginComponent.cpp
		    │   ├── MyPlugin.cpp
		    │   └── MyPlugin.Build.cs
		    │
		    │
		    └── MyPluginEditor/           # (Optional) Editor‑only module
		        ├── MyPluginEditor.Build.cs
		        ├── Public/
		        │   └── MyPluginEditorModule.h
		        └── Private/
		            └── MyPluginEditorModule.cpp

In addition, we noticed that making changes to a plugin isn't seen by the compiler and <span class="blue">live-coding</span> until we restart the project. We don't want to be wasting our time restarting so we notify live-coding about our dll:

1. **Module Bootstrap**
    - Implement a minimal module class by subclassing `IModuleInterface` in `MyPlugin.cpp`
    - Define `StartupModule()` and `ShutdownModule()`—this ensures your plugin DLL loads at the right time and isn’t immediately unloaded. Add logs so we can see if it actually loads.
        
2. **<span class="red">Hot‑Reload</span> vs. <span class="blue">Live Coding</span>**
    - **Hot‑Reload** (the in‑editor “Compile” button) can fail to pick up changes in plugin modules because the engine unloads their DLLs.
    - **Live Coding** is designed for iterative workflow:
        - Add a `"LiveCodingModules"` array to your `.uproject`, listing each plugin module name. <span class="red">Not sure if this is necessary</span>
        - Trigger a Live‑Coding compile—you’ll see those DLLs rebuild and reload without restarting the editor.
3. Add the bin to the <span class="red">PATH</span> (not as its own Environment Variable)

## Still not loading Plugin
You will want to load the plugin when the game starts and the recompile using Live Coding. We can do this by adding the following code to a BeginPlay somewhere:
```cpp
  FModuleManager::Get().LoadModuleChecked(TEXT("MyPlugin"));
  UE_LOG(LogTemp, Log, TEXT("MyPlugin module loaded from anywhere"));
```
I added it to the <span class="green">GameMode</span> used in the project, which is also set in the world settings as the GameMode.

## Not loading changes to plugin with Live Coding
For some reason the loading of the plugin and reloading after changes works better if I run Unreal via the <span class="green">IDE</span>.

## Making blueprint callable C++ code
With the plugin in place and the ability to modify and recompile quickly, we can make functions in C++ that are callable from blueprints:
[[Blueprint callable C++ and variables from bp in C++]]

## If a plugin relies on another plugin
**Check your plugin descriptor** (`myplugin.uplugin`) to ensure it has the other plugin's module listed, example:
```json
"Plugins": [ { "Name": "LiveLink", "Enabled": true } ]
```
Also don't forget to clean and build.
