#UnrealEngine #UnrealPython #RemoteControl #OSC #PIE
###  3 ways to drive UE from Python / external apps

| Method                       | Runs where                         | Setup                              | Latency  | Ship in packaged |
| ---------------------------- | ---------------------------------- | ---------------------------------- | -------- | ---------------- |
| Editor Python “tick”/loop    | **Editor/PIE only**                | none                               | low      | ❌                |
| Remote Control API (HTTP/WS) | Editor/PIE/Standalone/**Packaged** | expose function in Preset          | low–med  | ✅                |
| OSC (UDP)                    | Editor/PIE/Standalone/**Packaged** | enable OSC + small BP/C++ receiver | very low | ✅                |

### 1) PythonUnreal
We can hook into the tick and other places by doing something like:
```python
self.slate_post_tick_handle = unreal.register_slate_post_tick_callback(self.tick)
```
[Failed to connect to Unreal Engine [Troubleshooting] · nils-soderman/vscode-unreal-python Wiki](https://github.com/nils-soderman/vscode-unreal-python/wiki/Failed-to-connect-to-Unreal-Engine-%5BTroubleshooting%5D)

### 2) Remote Control API
The benefit is that we can call UFUNCTIONs from an external Python process. So we don't need the Python script to hook into Unreal. This eliminates freezes due to handling python in an update function and it also helps with the overhead that comes with changing codebases to fit Unreal Engine.

**UE Setup (once):**
1. Enable **Remote Control API** plugin.
2. Window → **Remote Control** → create **Preset**.
3. Add your actor/component and **Expose** the function (e.g., `UpdateSign(Sign, Confidence)`).
4. Ensure **Remote Control** server is enabled (Project Settings → Remote Control).

**External Python example:**
```python
import requests
URL = "http://127.0.0.1:30010/remote/preset/MyPreset/function/UpdateSign"
payload = {"Parameters": {"Sign": "HELLO", "Confidence": 0.92}}
requests.put(URL, json=payload, timeout=2).raise_for_status()
```

### 3) OSC
**UE Setup:**
1. Enable **OSC** plugin.
2. Project Settings → **OSC** → add a **Server** (e.g., port **8000**).
3. In a BP or C++ actor, add an **OSC Receiver** and handle `/sign/update` → call `UpdateSign`.

## PIE vs Editor world (and how to get them in Python)
When you run PIE, Unreal spawns a **separate play world**. Your editor-time actors are _duplicated_ into this runtime world. If you want to poke the _actual running_ instance during PIE, you must target the **game world**, not the editor world.
```python
import unreal

def get_current_world(require_game_world=False):
    ues = unreal.get_editor_subsystem(unreal.UnrealEditorSubsystem)
    if ues:
        w = ues.get_game_world()
        if w:
            return w
        if not require_game_world:
            return ues.get_editor_world()
    if require_game_world:
        raise RuntimeError("No game world available (not in PIE/SIE).")
    return None
```
