#UnrealEngine #CPP #UnrealPython 
In order to <span class="blue">combine C++ with blueprints</span>, we need to somehow expose the C++ to the blueprints:

- **Functions exposed to Blueprints** need `UFUNCTION()` with specifiers like `BlueprintCallable` or `BlueprintPure`.
- **Variables visible in the Editor or Blueprints** need `UPROPERTY()` with specifiers like:
    - `VisibleAnywhere`, `EditAnywhere` → for editor visibility.
    - `BlueprintReadOnly`, `BlueprintReadWrite` → for Blueprint access.
- `UFUNCTION` specifiers go **on functions**, `UPROPERTY` specifiers go **on member variables** (not on functions).


In addition to exposing C++ to blueprints, we can also change exposed variables in the blueprint which is in turn used in the C++:
1. **Define the variable in C++** using `UPROPERTY()` with the right specifiers.
2. **Edit the value in Blueprint** (in an Actor or Component).
3. **Access that value in your C++ code** at runtime.

It is important to note that <span class="blue">Python</span> can call Blueprint-exposed stuff (Editor/PIE)

We can also do <span class="green">Events</span> in C++, similar to Unity.
In C++ we can do the following or something similar:
```cpp
// In header
DECLARE_DYNAMIC_MULTICAST_DELEGATE_TwoParams(FAzureActiveBodyChanged, int32, OldBodyId, int32, NewBodyId);

UPROPERTY(BlueprintAssignable, Category="Events")
FAzureActiveBodyChanged OnActiveBodyChanged;

// later in cpp:
OnActiveBodyChanged.Broadcast(OldId, NewId);
```
Now this filed is added to the component (usually under class defaults "Events").
