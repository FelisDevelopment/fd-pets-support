# Companions / Pets system
Custom pets resource, designed to work as standalone resource or be dynamic to be able to adapt it to any framework.

### Support
Any issues / Bugs or Suggestions has to be reported in this repository issues. Please refer to: [Issues](https://github.com/FelisDevelopment/fd-pets-support/issues)

### Purchase / Preview
System can be purchased at [Tebex](https://felis-development.tebex.io)
Preview of this resource can be found on [Youtube](https://youtube.com)

##### QBCore
If you use [QBCore](https://github.com/qbcore-framework) for your server, you can find this system simple adaption for free at [repository](https://github.com/FelisDevelopment/fdqb-pets). (fd-pets is still needed as a dependency)

# Documentation

### [Config](docs/Config.md) explanation
### [Translations](docs/Translations.md) explanation

### Exports
#### Client
##### Setters

| Export              | Description                 | Parameter(s) |
|---------------------|-----------------------------|--------------|
| [SpawnPet](docs/client/SpawnPet.md)    | Spawn pet          | string  |
| [OverrideMethod](docs/client/OverrideMethod.md)     | Without going to main dependency, you can override various utility methods           | string, function          |
| [AddOrOverrideCustomMethod](docs/client/AddOrOverrideCustomMethod.md)      | Add or override existing custom actions            | string, function          |
| [ForceCloseMenu](docs/client/ForceCloseMenu.md)        | Forcefully close pet actions menu  |           |

##### Getters
| Export              | Description                 | Return Type |
|---------------------|-----------------------------|--------------|
| [DoesPetExist](docs/client/DoesPetExist.md)    | Check if client has a pet spawned and it exists and is alive          |  bool or int  |
| [IsMenuOpen](docs/client/IsMenuOpen.md)      | Check if pet actions menu is open |  bool        |+

#### Server
##### Setters

| Export              | Description                 | Parameter(s) |
|---------------------|-----------------------------|--------------|
| [OverrideMethod](docs/server/OverrideMethod.md)     | Without going to main dependency, you can override various utility methods           | string, function          |

##### Getters
| Export              | Description                 | Return Type |
|---------------------|-----------------------------|--------------|
| [HasActivePet](docs/server/HasActivePet.md)    | Check if client has a pet active pet        |  bool or int  |

### Events
#### Client

| Event                    | Description                                                  |
|--------------------------|--------------------------------------------------------------|
| [fd-pets:actions:spawnpet](docs/client/EventsSpawnPet.md) | Pet can be spawned with this event |
### Subscribable events
You can subscribe to these events if you want to something after they're triggered.

#### Server

| Event                    | Description                                                  |
|--------------------------|--------------------------------------------------------------|
| [fd-pets:server:entityDead](docs/server/EventsEntityDead.md) | When triggered, it means pet / entity doesn't exist anymore, is out of scope or died |
| [fd-pets:server:recallPet](docs/server/EventsRecallPet.md) | When triggered, it means pet is being recalled |

### Adding new animation to menus. Refer to: [AddNewAnimation](docs/AddNewAnimation.md)
### Adding new custom action to menus. Refer to: [AddCustomAction](docs/AddCustomAction.md)
