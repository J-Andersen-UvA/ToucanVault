#UnrealEngine #Blueprint 
### Unreal Editor Utility – Transactions (Undo Support)
- Can’t use Ctrl+Z? Or too much stuff to Ctrl+Z? Wrap the function in a **Transaction**.
- Use **Begin Transaction** to start the wrap.
- Use **End Transaction** to finish it → everything inside becomes undoable.

### Begin Transaction Parameters
- **Context:** Internal category/name used to group the transaction.
- **Description:** Text shown in the Undo History.
- **Primary Object:** Main object being modified (can be left `null`).
