# Components


## Saveable\<T>

Arcade Idle Engine contains a lot of Scriptable Objects, some of them is just plain data holder but others have functionality as well. Saveable contains generic implementation for creating save datas. These datas can be saved into and loaded from the disk. Initial value can be set if there isn't any save file.

Two concerete implementations can be found in the asset:
**`Int Variable`** and **`UniqueIntListVariable`**.


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

