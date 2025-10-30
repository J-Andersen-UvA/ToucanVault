#Blueprint #UnrealEngine #TroubleShooting 

- build errors due to zombies
- [[UE Plugin & Live‑Coding Setup]]
- [[UE Plugin & Live‑Coding Setup#Help where are my blueprint nodes!]]

LINK error, do you have the module export/import macro? Something like (<span class="blue">TOUCANSESSIONSEQUENCER_API</span>):
```cpp
class TOUCANSESSIONSEQUENCER_API FEditingSessionSequencerHelper
```
