## Adding custom action which is perfomed with provided method

## Description

You can easily add new action which is totaly custom for specific animal. Please compare examples below to see how it's done. `foo` action will be added.

## File

* **shared/config.lua**

## Added new animation for pet

```lua
    ["rottweiler1"] = {
        ["model"] = "a_c_rottweiler",
        ["actions"] = {
            ["move"] = {"selection", "player", "vehicle"},
            ["sit"] = {"base", "selection"},
            ["follow"] = {"base", "selection", "player", "ped", "vehicle"},
            ["break"] = {"base", "selection"},
            ["wander"] = {"base", "selection"},
            ["taunt"] = {"base", "selection"},
            ["beg"] = {"base", "selection"},
            ["paw"] = {"base", "selection"},
            ["dead"] = {"base", "selection"},
            ["attack"] = {"selection", "player", "ped"},
            ["getout"] = {"invehicle"},
            ["getin"] = {"vehicle"},
            -- new action `foo`, which will be shown only in base and selection menus
            ["foo"] = {"base", "selection"}
        },
        ["followOnSpawn"] = true,
        ["animations"] = {
            ["calling"] = {
                ["dict"] = "taxi_hail",
                ["anim"] = "hail_taxi"
            },
            ["sit"] = {
                ["dict"] = "creatures@rottweiler@tricks@",
                ["anim"] = "sit_loop"
            },
            ["sitInCar"] = {
                ["dict"] = "creatures@rottweiler@in_vehicle@std_car",
                ["anim"] = "sit"
            },
            ["break"] = {
                ["dict"] = "creatures@rottweiler@amb@sleep_in_kennel@",
                ["anim"] = "sleep_in_kennel"
            },
            ["taunt"] = {
                ["dict"] = "creatures@rottweiler@melee@streamed_taunts@",
                ["anim"] = "taunt_02"
            },
            ["beg"] = {
                ["dict"] = "creatures@rottweiler@tricks@",
                ["anim"] = "beg_loop"
            },
            ["paw"] = {
                ["dict"] = "creatures@rottweiler@tricks@",
                ["anim"] = "paw_right_loop"
            },
            ["dead"] = {
                ["dict"] = "creatures@rottweiler@move",
                ["anim"] = "dead_left"
            },
        },
        ["skin"] = {
            -- componentId, drawableId, textureId, paletteId
            {4, 0, 0, 0}
        }
    }
```

## After adding changes to config file, please refer go `client/customActions.lua` file and your custom action
```lua
-- Remember that method name (key) has to be same as defined in config, in our example it's `foo`
customActions.foo = function(pet, config, selected, state)
    state = not state

    changeState("foo", state)

    -- If current state is true, let's do action
    if state then
        -- Let's clear current tasks
        ClearPedTasksImmediately(NetToPed(pet))

        -- in this example let's just make pet to look at a player, selected or just an owner if entity isn't selected
        local lookAt = PlayerPedId()

        if selected.entity then
            lookAt = selected.entity
        end

        TaskLookAtEntity(NetToPed(pet), lookAt, -1, 2048, 3)

        return
    end

    -- Otherwise if same action pressed, let's clear current tasks
    ClearPedTasks(NetToPed(pet))
end
```
