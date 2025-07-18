#UnrealEngine #CPP
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

