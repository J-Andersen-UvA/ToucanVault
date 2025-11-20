#Blueprint #UnrealEngine #TroubleShooting 

### Common issues
- build errors due to zombies
- [[UE Plugin & Live‑Coding Setup]]
- [[UE Plugin & Live‑Coding Setup#Help where are my blueprint nodes!]]

### LINK error
Do you have the module export/import macro? Something like (<span class="blue">TOUCANSESSIONSEQUENCER_API</span>):
```cpp
class TOUCANSESSIONSEQUENCER_API FEditingSessionSequencerHelper
```

### Need to <span class="red">build twice</span> issue:
Deleting `Binaries/`, `Intermediate/`, and `Saved/` (or running `-Clean`) forces a **cold rebuild**.  
That removes all stale object files and ensures the next compile links against fresh code.

1. Close Visual Studio.
2. Delete:
    `<Project>/Saved/ <Project>/.vs/ <Project>/Intermediate/ <Project>/Binaries/ <Project>/Plugins/<YourPlugin>/Intermediate/ <Project>/Plugins/<YourPlugin>/Binaries/ C:\Users\<you>\AppData\Local\UnrealBuildTool\`
3. Reopen `.uproject`, let Unreal regenerate solution files (`right-click → Generate Visual Studio project files`).
4. Build once directly from the **Unreal Editor** (not VS).
5. If that succeeds, future VS builds will be consistent.

After that, it will work normally until Unreal again caches or locks an old DLL—typically after Live Coding use or long sessions without restarting the editor.
