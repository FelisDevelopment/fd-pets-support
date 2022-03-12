## Adding custom animation to actions

## Description

You can easily add new animations for specific animal. Please compare examples below to see how it's done. `example` animation will be added.

## File

* **shared/config.lua**

## Current unchanged config
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
            -- new action `example`, which will be shown only in base and selection menus
            ["example"] = {"base", "selection"}
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
            -- since this example the action `example` is not custom method, we'll add animation which will be applied for entity
            ["example"] = {
                ["dict"] = "example@dict@very@much",
                ["anim"] = "example"
            },
        },
        ["skin"] = {
            -- componentId, drawableId, textureId, paletteId
            {4, 0, 0, 0}
        }
    }
```
