## OverrideMethod

## Description

You can override original Utils methods from any resource.

## Parameters

* **method**: available overrides: CanPlayerSpawnPet, OnEntityDiedOrDoesntExist, OnPetAlreadyExists, OnEntityRecalled
* **callback**: method to be used, properties provided to method depends on method


## Parameters passed to callback

#### CanPlayerSpawnPet - Triggered whenever player tries to spawn a pet (needs to return bool)
* **source**: int - player source
* **pet**: string - original pet (config key)
* **config**: table - original config

#### OnEntityDiedOrDoesntExist - Triggered whenever entity is reported dead or doesnt exist
* **source**: int - player source
* **entity**: int - local entity id

#### OnPetAlreadyExists - Triggered whenever pet was tried to spawn but it player already has one spawned
* **source**: int - player source
* **pet**: string - original pet (config key)
* **config**: table - original config
* **entity**: int - local entity id

##### OnEntityRecalled - Triggered whenever pet was recalled
* **source**: int - player source
* **entity**: int - local entity id

## Examples

```lua
exports['fd-pets']:OverrideMethod("CanPlayerSpawnPet", function(source, pet, config)
    -- Do something and return bool

    return true
end)
```
