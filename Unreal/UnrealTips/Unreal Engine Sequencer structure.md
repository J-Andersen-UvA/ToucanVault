#UnrealEngine #Sequencer 
Accessing various parts in the sequencer is not hard as long as you understand the structure of the sequencer.

Sequence --> Bound objects --> Tracks --> Sections
### Sequence
We have a sequence itself, it can be stored as an asset or loaded into the scene. When we open it we have an active sequence that we can access through:
```cpp
// implement code example
```

### Bound objects
Objects that we bind to the sequence, like skeletalmeshes for example, are accessible through their Guid. When we add an asset to the sequence, or we bind it from the scene to the sequence, we get a Guid that we use to access it inside the sequence.
```cpp
// implement code example
```

### Tracks
For a bound object inside the sequence, we can add tracks. For example, a bound skeletalmesh can have a track such as the moviesceneskeletalanimation (<span class="red">Double check name</span>). We can do various stuff with a track, but it is mostly used as a container for the actual assets or actions that we perform on the bound object. Not all bound objects can hold multiple identical tracks. For example I found that the animation track was displaying odd behaviour when trying to add multiple.
```cpp
// implement code example
```

### Sections
A track can have multiple sections. And a section can contain multiple things. For the animation section for example, it can hold multiple animations. But we could also add multiple animation sections to the animation track, enabling us to play multiple animations on a single bound object.
```cpp
// implement code example
```
