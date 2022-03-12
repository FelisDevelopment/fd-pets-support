## Config basics

## Description

Config contains to tables, `General` and `Animals`. Let's talk about both of them.
NOTE: in example there will be used only few parts of config, to see it fully, please refer to original file.

I'll leave comments for a config file down below, if you don't understand something, please open an issue for better explanation.

## File

* **shared/config.lua**

##

```lua
General = {
    ["debug"] = false, -- enables some prints for debuging resource
    ["selectionDistance"] = 30.0, -- distance which will be used for selection how far away can coords or entity be
    ["timeouts"] = {
        ["beforeRemovingPet"] = 20 * 1000, -- Timeout before dead / not existing entity is deleted since it's server sided
        ["beforeAllowingToSpawnNewPet"] = 30 * 1000, -- Timeout before user can spawn new pet (after it died)
        ["respawnTimeoutEnabledOnRecall"] = false -- enables respawn timeout whenever pet was recalled by player and not died
    },
    ["binds"] = {
        ["enabled"] = true, -- enables custom binds for two different menu
        ["action"] = { -- start selection menu, first you'll have to select point in map or entity, after second click menu will show up
            ["defaultBind"] = "",
            ["text"] = "Start selecting actions"
        },
        ["actionWithoutSelection"] = { -- will open base menu without specific selection coords or entity
            ["defaultBind"] = "",
            ["text"] = "Open pet menu"
        }
    },
    ["commands"] = {
        ["spawn"] = { -- basic spawn command, mainly focused to be standalone
            ["enabled"] = false, -- disable or enable command
            ["command"] = "spawnpet", -- rename command
            ["useAce"] = true -- will you use ace permissions for it?
        }
    }
}

Animals = {
    ["rottweiler1"] = { -- key by which animal will be identified
        ["model"] = "a_c_rottweiler", -- probably obvious one
        ["actions"] = { -- here you will define actions which will be provided to different type menus
            -- Available menus:
            ---- base - base menu opened whenever there's no entity or coords selected
            ---- selection - selection menu opened whenever there's a second click after selecting specific point in map or entity
            ---- vehicle - opened whenever vehicle is selected
            ---- player - opened whenever player is selected
            ---- ped - opened whenever ped is selected
            ---- invehicle - opened whenever pet is in vehicle
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
            ["getin"] = {"vehicle"}
        },
        ["followOnSpawn"] = true, -- follow player automatically whenever pet is spawned
        ["animations"] = {
            ["calling"] = { -- this animation will be called on a player
                ["dict"] = "taxi_hail",
                ["anim"] = "hail_taxi"
            },
            ["sit"] = {
                ["dict"] = "creatures@rottweiler@tricks@",
                ["anim"] = "sit_loop"
            },
            ["sitInCar"] = { -- sitInCar will be used for sitting animation in vehicle (if not provided, it'll fallback to "sit" animation)
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
            -- Skin can be applied whenever pet is spawned (multiple tables accepted since we'll itterate over them)
            -- componentId, drawableId, textureId, paletteId
            {4, 0, 0, 0}
            -- {2, 1, 0, 0}
        }
    }
}
```
