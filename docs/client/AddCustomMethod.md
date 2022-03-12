
## AddOrOverrideCustomMethod

## Description

You can add or override custom methods for actions via this export.

## Parameters

* **method**: method name
* **callback**: method to be used

## Parameters passed to callback
* **netId**: int - pet network id
* **config**: table - original config
* **selected**: table - table with selection (entity, coords)
* **currentActionState**: bool - current action state

## Examples

```lua
-- this methods is already added to client/customActions.lua, but we will use it as an example
exports['fd-pets']:AddOrOverrideCustomMethod("wander", function(pet, config, selected, state)
    state = not state

    changeState("wander", state)

    if state then
        ClearPedTasksImmediately(NetToPed(pet))

        local coords = GetEntityCoords(NetToPed(pet), true)
        TaskWanderStandard(NetToPed(pet), 10.0, 10)
        SetPedKeepTask(NetToPed(pet), true)

        return
    end

    ClearPedTasks(NetToPed(pet))
end)
```
