## Translations

## Description

Since I wanted to make resource as dynamic as possible, resource provides very basic translations with very structure for it.
If you add a new action(it doesn't matter if it's an animation or a custom method for action). There's very simple syntax to add translation as well.

So let's say you add action called `example`. Whenver looking up for action title, first letter will be converted to upper case, and checked within translations table, so at the end, code will search for `"Example"` key in Translations table, if it's not found it'll fallback to upper cased key and return it to be provided for menu.

Helptext can be added also, simple syntax: code will take upper cased key and add `Helptext` with a space. In the end, code will look for `Example Helptext` key in translations table. If it's not found, it'll be skipped and empty string returned.

Please refer to example down below.

## File

* **shared/translations.lua**

## Current file structure

```lua
Translations = {
    ["MenuTitle"] = "Pet Actions",
    ["MenuSubtitle"] = "Choose action down below",
    ["Pet has been recalled."] = "Pet has been recalled.",
    ["Animal config wans't found. Please contact your administrator!"] = "Animal config wans't found. Please contact your administrator!",
    ["Pet has been called."] = "Pet has been called.",
    ["Cannot retreive pet config. Please contact administrator!"] = "Cannot retreive pet config. Please contact administrator!",
    ["Animation wasn't found. Please contact your administrator!"] = "Animation wasn't found. Please contact your administrator!",

    -- Dynamic translations below
    ["Move"] = "Move",
    ["Move Helptext"] = "Move to this position",
    ["Follow"] = "Follow",
    ["Follow Helptext"] = "Follow selected thingy",
    ["Sit"] = "Sit",
    ["Sit Helptext"] = "Put that ass down",
    ["Break"] = "Lay Down",
    ["Break Helptext"] = "Take a short nap",
    ["Wander"] = "Wander",
    ["Wander Helptext"] = "Let 'em be",
    ["Dead"] = "Play Dead",
    ["Dead Helptext"] = "Pretend to be dead and trick someone",
    ["Taunt"] = "Taunt",
    ["Taunt Helptext"] = "They need to be scared",
    ["Beg"] = "Beg",
    ["Beg Helptext"] = "Beg for 'em treats",
    ["Paw"] = "Paw",
    ["Paw Helptext"] = "Say hello, without biting that ass",
    ["Attack"] = "Attack",
    ["Attack Helptet"] = "Bite that ass",
    ["Getin"] = "Get in",
    ["Getin Helptext"] = "Get in that vehicle",
    ["Getout"] = "Get out",
    ["Getout Helptext"] = "Get out that vehicle",
    ["Sleep"] = "Sleep",
    ["Sleep Helptext"] = "Everybody needs to sleep",
    ["Idle"] = "Idle",
    ["Idle Helptext"] = "Literally do nothing",
    ["Peck"] = "Peck",
    ["Peck Helptext"] = "I guess sidewalk or a road tastes good also",
}
```

## With added new translation

```lua
Translations = {
    ["MenuTitle"] = "Pet Actions",
    ["MenuSubtitle"] = "Choose action down below",
    ["Pet has been recalled."] = "Pet has been recalled.",
    ["Animal config wans't found. Please contact your administrator!"] = "Animal config wans't found. Please contact your administrator!",
    ["Pet has been called."] = "Pet has been called.",
    ["Cannot retreive pet config. Please contact administrator!"] = "Cannot retreive pet config. Please contact administrator!",
    ["Animation wasn't found. Please contact your administrator!"] = "Animation wasn't found. Please contact your administrator!",

    -- Dynamic translations below
    ["Move"] = "Move",
    ["Move Helptext"] = "Move to this position",
    ["Follow"] = "Follow",
    ["Follow Helptext"] = "Follow selected thingy",
    ["Sit"] = "Sit",
    ["Sit Helptext"] = "Put that ass down",
    ["Break"] = "Lay Down",
    ["Break Helptext"] = "Take a short nap",
    ["Wander"] = "Wander",
    ["Wander Helptext"] = "Let 'em be",
    ["Dead"] = "Play Dead",
    ["Dead Helptext"] = "Pretend to be dead and trick someone",
    ["Taunt"] = "Taunt",
    ["Taunt Helptext"] = "They need to be scared",
    ["Beg"] = "Beg",
    ["Beg Helptext"] = "Beg for 'em treats",
    ["Paw"] = "Paw",
    ["Paw Helptext"] = "Say hello, without biting that ass",
    ["Attack"] = "Attack",
    ["Attack Helptet"] = "Bite that ass",
    ["Getin"] = "Get in",
    ["Getin Helptext"] = "Get in that vehicle",
    ["Getout"] = "Get out",
    ["Getout Helptext"] = "Get out that vehicle",
    ["Sleep"] = "Sleep",
    ["Sleep Helptext"] = "Everybody needs to sleep",
    ["Idle"] = "Idle",
    ["Idle Helptext"] = "Literally do nothing",
    ["Peck"] = "Peck",
    ["Peck Helptext"] = "I guess sidewalk or a road tastes good also",
    -- Added new action or animation
    ["Example"] = "Example action",
    ["Example Helptext"] = "Example action helptext, which could be empty so nothing would be displayed"
}
```
