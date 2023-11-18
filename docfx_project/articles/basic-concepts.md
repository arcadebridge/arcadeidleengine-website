# Basic Concepts


## Save System
Arcade Idle Engine contains a lot of ScriptableObjects, some of them is just plain data holder but others have functionality as well. ScriptableObjects derived from Saveable contain implementation for saving data. These data can be saved and loaded from the disk. Initial value can be set if there isn't any save file. These `Saveable` objects can be saved by `SaveManager` class. 

Two concrete implementations can be found in the asset:
`Int Variable` and `UniqueIntListVariable`.

Saving tool list is more complex because it's needed to save their indexes. `UniqueIntListVariable` can be used to save their indexes. And then `GatheringToolDefinitionIndexLookup` can be used along with `GatheringToolDatabase` for indexing every gathering tool. 

You can also extend classes to create your own implementation by creating your own custom implementation that derives from `ObjectDatabase` and `IndexLookup` or `Saveable<T>`.

> [!TIP]
> When working in Unity Editor, you might want to disable the `Save Automatically` feature in the `Automatic Save Load` GameObject inside the `Booting` scene in order to test things quickly. Otherwise, you would have to delete the save file and set the initial value for the `Current Level` variable to load the desired scene. If you want to learn more, head to the `Booting` section.

> [!TIP]
> There is also a `SaveUpgrader` class that handles new Save versions. If you need to learn more about this Save Versioning concept, you can find a lot of explanations on the internet.


You need to assign Saveables to the `SaveManager` so it can save and load them when the game runs. Use SaveManager to save your game state like collected wood count or money.

Use `Tools > HypercasualPack > Open Save Directory` if you want to delete the save file or modify it manually.


## Booting
Booting scene has a collection of GameObjects for initializing the game. It waits for the loading save data (and possibly by your custom scripts other types of initialization too like SDK initializations, or fetching remote config data). Then `GameBooter` uses `IntVariable` to get the latest current level we are in and use that for loading a new level. When you hit play in the Editor (and in the runtime as well) the Booting scene will be loaded first, and then the Booting scene will load the scene by using an index that is coming from the current level variable.


## Pickable
It mostly works as a tag, but it has an important Pickable Definition asset, which contains things like sell value and visibility properties (which sets whether it should be visible or not when we pick it).


## PickableSellers
It sells desired pickables by using their sell value and sellable properties. There are 2 kinds of Sellers. One is **`Pickable Seller Floating Text`** and the other is **`Pickable Seller Floating Image`**


## ResourceMonitorVisualizer
Contains pooled object and resource to modify when we earn stuff. It's a pretty common effect where when you earn money, money image appears on the screen and goes to the money UI (usually it sits at the top of the screen).     
         
         
## IntVariableMonitor     
**Int Variable Monitor** is for updating the text based on the variable it listens to.


## ResourceTargetImage
ResourceTargetImage is for registering the object to the scriptable object so ResourceMonitorVisualizer knows where spawned objects should arrive.


## PickableSourceSpawner
Spawns Pickable gameObjects using a pool. Can be configured by adjusting properties like spawnInterval and pickingTime.


## PickableDefinition
kopkopkk


## PickableCollectorStockpiler
The script defines a class responsible for collecting, modifying, and stockpiling pickable items based on specified rules and timers. It manages the flow of items between unmodified and modified states, with an upgradeable work speed affecting the modification process. The class employs coroutines and timers to control item collection and processing.


## PickableCollectorMultipleCondition
Same as the PickableCollectorStockpiler but
