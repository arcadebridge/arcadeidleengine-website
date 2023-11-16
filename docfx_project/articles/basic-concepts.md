# Basic Concepts


## Save System
Arcade Idle Engine contains a lot of ScriptableObjects, some of them is just plain data holder but others have functionality as well. ScriptableObjects derived from Saveable contains implementation for save datas. These datas can be saved into and loaded from the disk. Initial value can be set if there isn't any save file. These `Saveable` objects can be saved by `SaveManager` class. 

Two concerete implementations can be found in the asset:
`Int Variable` and `UniqueIntListVariable`.

Saving tool list is more complex because it's needed to save their indexes. `UniqueIntListVariable` can be used to save their indexes. And then `GatheringToolDefinitionIndexLookup` can be used along with `GatheringToolDatabase` for indexing every gathering tool. 

You can also extend classes to create your own implementation by creating your own custom implementation that derives from `ObjectDatabase` and `IndexLookup` or `Saveable<T>`.


## Booting
Booting is a collection of tools for initializing the game. It waits for the loading save data and possibly other types of initialization too (like SDK initializations, or fetching remote config data). Then `GameBooter` uses `IntVariable` to get the latest current level we are in and use that for loading new level.

### Advanced Topics
There is also a `SaveUpgrader` class which handles new Save versions. If you need to learn more about this Save Versioning concept, you can find a lot of explanations in the internet.


## SaveManager
You need to assign Saveables to the Save Manager so it can save and load them when game runs. Use Save Manager for saving your game states like collected wood count or money.

Use `Tools > HypercasualPack > Open Save Directory` if you want to delete the save file or modify manually.


## Pickable
It mostly works as a tag, but it has an important Pickable Definition asset, which contains things like sell value and visiblity properties (which sets whether it should be visible or not when we pick it).


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
kopkop


## PickableCollectorStockpiler
The script defines a class responsible for collecting, modifying, and stockpiling pickable items based on specified rules and timers. It manages the flow of items between unmodified and modified states, with an upgradeable work speed affecting the modification process. The class employs coroutines and timers to control item collection and processing.


## PickableCollectorMultipleCondition
Same as the PickableCollectorStockpiler