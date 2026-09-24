# Pose generation
from hamnosys there is a mark up language that is similar: sigml and that is used to generate poses (for example: [CoffeeScript WebGL ARP Signing Avatar: vhg.2026](https://vhg.cmp.uea.ac.uk/tech/jas/vhg2026/cwa/OneAvClient.html))
It seems rather robotic

### Interperters
How do they decide on the translation? Because its not one to one.
How do you then decide on the face mimicry.

# Retargeting system specific to Sign Language
Based on location areas, handshapes that you will have to redefine for the target avatar.
Basically you define stuff on the target avatar and base avatar, and you retarget based on that instead of the rotations.
Therefore it closely follows ReConForM
Develop DLL separate from Unreal and then build layer in unreal? Maybe we can separate it into:
**Math library:** "Give me numbers and gradients; I'll optimize them."
**Context solver:** "These numbers happen to be joint rotations, and here's how they produce anchor positions and losses."
**Unreal plugin:** "These joints happen to correspond to Unreal bones."
# Blendshape recording system specific to sign language
Perhaps we can train something to recognize the oral components on faces (or even specific persons face) and then we can pick the correct blendshapes ourselves instead of LLF.

# HamNoSys Picker
HamNoSys picker for sign language animation data.

# Signbank glosses + videos -> HamNoSys
We could maybe combine videos and glosses to hamnosys.

