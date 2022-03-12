## OverrideMethod

## Description

You can override original Utils methods from any resource.

## Parameters

* **method**: available overrides: OnTryingToSpawnPet, OnFinishingPetSetup, OnOpeningMenu, OnStartingAction, Notification
* **callback**: method to be used, properties provided to method depends on method

## Parameters passed to callback

#### OnTryingToSpawnPet - Triggered whenever player tries to spawn a pet
* **pet**: string - original pet (config key)
* **config**: table - original config

#### OnFinishingPetSetup - Triggered whenever pet is already spawned and set up for it is finishing
* **netId**: int - pet network id
* **config**: table - original config
* **pet**: string - original pet (config key)

#### OnOpeningMenu - Triggered whenever player is trying to open menu
* **config**: table - original config
* **selected**: table - table with selection (entity, coords)

##### OnStartingAction - Triggered whenever action for pet is triggered
* **action**: string - triggered action
* **netId**: int - pet network id
* **config**: table - original config

##### Notification - Override notification depending on your systems
* **text**: string - notification text
* **type**: string - notification type (success, error)

## Examples (from QBCore adaptation script)

```lua
exports['fd-pets']:OverrideMethod("OnTryingToSpawnPet", function(pet, config)
    local retval = nil

    QBCore.Functions.TriggerCallback('QBCore:HasItem', function(hasItem)
        if hasItem then
            retval = true
        else
            retval = false
        end
    end, pet)

    while retval == nil do
        Wait(0)
    end

    return retval
end)

```lua
exports['fd-pets']:OverrideMethod("OnStartingAction", function(action, netId, config)
    -- Something something
end)
```

```lua
exports['fd-pets']:OverrideMethod("OnOpeningMenu", function(config, selected)
    local PlayerData = QBCore.Functions.GetPlayerData()

    if not PlayerData.metadata["isdead"] and not PlayerData.metadata["inlaststand"] and not PlayerData.metadata["ishandcuffed"] and not IsPauseMenuActive() then
        return true
    end

    return false
end)
```
