To add a custom **dropdown menu** with **buttons** in the Unreal Editor:
#### 1. Extend a main menu

Use `UToolMenus::Get()->ExtendMenu("LevelEditor.MainMenu")` to attach your menu under _File/Edit/etc._
```cpp
void FMyModule::RegisterMenus()
{
    FToolMenuOwnerScoped OwnerScoped(this);
    UToolMenu* MainMenu = UToolMenus::Get()->ExtendMenu("LevelEditor.MainMenu");

    FToolMenuSection& Section = MainMenu->FindOrAddSection("MyToolsRoot");

    Section.AddSubMenu(
        "MyToolsMenu",
        LOCTEXT("MyTools", "My Tools"),
        LOCTEXT("MyTools_Tooltip", "Custom utilities"),
        FNewToolMenuDelegate::CreateRaw(this, &FMyModule::BuildMyMenu)
    );
}
```
#### 2. Build the submenu (add buttons)
Each entry is a button that runs a function via `FUIAction`.
```cpp
void FMyModule::BuildMyMenu(UToolMenu* Menu)
{
    FToolMenuSection& Section = Menu->AddSection("MyToolsSection", LOCTEXT("MyToolsSection", "My Tools"));

    Section.AddMenuEntry(
        "DoSomething",
        LOCTEXT("DoSomething", "Do Something"),
        LOCTEXT("DoSomething_Tooltip", "Runs a custom action."),
        FSlateIcon(),
        FUIAction(FExecuteAction::CreateRaw(this, &FMyModule::OnDoSomething))
    );
}
```

#### 3. Bind your action
```cpp
void FMyModule::OnDoSomething()
{
    UE_LOG(LogTemp, Log, TEXT("Button clicked!"));
}
```


💡 **In short:**
- `ExtendMenu` → hook into an existing menu.
- `AddSubMenu` → create dropdown.
- `AddMenuEntry` → add clickable buttons bound to actions.
