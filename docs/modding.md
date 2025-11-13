# Modding

Modding is currently unofficially supported and is only made possible by the [BloodThief Mod Loader](https://github.com/olvior/bloodthief-mod-loader) by Olvior. It was initially developed for the demo, but it works just fine with the full game. Functions on both Windows and Linux.

Note that the mod loader also supports importing custom textures into [Trenchbroom](https://trenchbroom.github.io/), BloodThief's custom mapping tool.

To disable mods, rename override.cfg to anything else.

## Where to get mods

The best place for this at present is the [modding discord](https://discord.gg/hpAKq35FJf), but there are mods floating around that you can install. Hopefully a more centralised location can be decided upon once the modding community grows.

Install mods by dropping the zip into the Bloodthief/mods folder in your steam directory. The modloader should auto-create this.

The following are a selection of useful/fun mods that should work with the current version of the game. Feel free to suggest more.

* [CarlosFruitCup's Mod Collection](https://github.com/carlosfruitcup/My-Bloodthief-Mods)

* [FridgeManIO's Mod Collection](https://github.com/FridgeManIO/BloodThiefMods/releases/tag/V1.0.0)

* [NameGoesThere's Livebat multiplayer mod](https://github.com/NameGoesThere/livebat/)

* [Emma's TAS Mod](https://github.com/Luna5829/bloodthief-tas-mod)

## How to create your own mods

Note: To effectively create your own mods, you will want to obtain a copy of the BloodThief source code. The technique for this will not be disclosed in this guide.

* Carlosfruitcup's demo docs [Demo Modding Wiki](https://github.com/carlosfruitcup/bloodthief-modding-docs/wiki)

* Olivor's mod loader [readme](https://github.com/olvior/bloodthief-mod-loader?tab=readme-ov-file#how-to-create-a-mod)

Mods should be packed up as a .zip file, and should contain the following files as a minimum.

### Minimum Example

``` json title="manifest.json"
{
    "name": "Modname",
    "name_pretty": "Mod Name",
    "namespace": "ns",
    "version_number": "1.0.0",
    "description": "Mod Description",
    "dependencies": [],
    "incompatibilities": [],
    "authors": ["Author1"],
    "tags": ["cheats"],
    "description_rich": "Detailed Mod Description"
}
```

```gd title="mod_main.gd"
extends "res://addons/ModLoader/mod_node.gd"

func init():
	ModLoader.mod_log(name_pretty + " mod loaded")
```

### Working mod_main.gd example
A more complete mod_main.gd file would look like this. [Source](https://github.com/FridgeManIO/BloodThiefMods/blob/main/fridge-infiniteStoneBuff/mod_main.gd)

In the cases where you only have to set/inspect globally available variables, this approach is fine, if a little unoptimised.

```gd title="mod_main.gd"
extends "res://addons/ModLoader/mod_node.gd"

var stoneskin_enabled = Setting.new(self, "StoneSkin Enabled", Setting.SETTING_FLOAT, 1, Vector2(0, 1))

func init():
	ModLoader.mod_log(name_pretty + " mod loaded")

	settings = {
		"settings_page_name" = "Infinite StoneSkin",
		"settings_list" = [
			stoneskin_enabled
		]
	}

func _process(_delta):
	if is_instance_valid(GameManager.player):
		if stoneskin_enabled.value == 0.0:
			return
		GameManager.player.stone_skin_active = true
```

### Mod Override Example

In cases where you have to override local variables, or even functions, you will have to override the BloodThief code itself. As a simple example we will use the [zeroLHBloodCost](https://github.com/FridgeManIO/BloodThiefMods/tree/main/fridge-zeroLHBloodCost) mod.

The code for the scythe looks something like this post-nerf:
```gd title="scythe_interaction_behaviour.gd"
func can_dash(player: Player):
    return player.blood_amount >= 0.3 and _can_dash and not _dash_on_cooldown and !player.is_on_floor() and player.on_ground_ray.get_collider() == null
```
Pre-nerf, the scythe (life harvester) did not have a blood cost denoted by `player.blood_amount >= 0.3`. In this case, one solution to revert this nerf would be to overwrite this function like so:
```gd title="scythe_interaction_behaviour_override.gd"
extends "res://scripts/components/scythe_interaction_behavior.gd"

func can_dash(player: Player):
    return _can_dash and not _dash_on_cooldown and !player.is_on_floor() and player.on_ground_ray.get_collider() == null
```

The `extends` path denotes the location of the script in the BloodThief source code to be overwritten. Only this function will be changed.

To actually overwrite this function, some extra code is required in main.gd
```gd title="main.gd"
extends "res://addons/ModLoader/mod_node.gd"

func init():
	ModLoader.mod_log(name_pretty + " mod loaded")
	var scythe_interaction_behaviour_override = load(path_to_dir+"/scythe_interaction_behaviour_override.gd")
	scythe_interaction_behaviour_override.take_over_path("res://scripts/components/scythe_interaction_behavior.gd")
```

### Custom Scenes Example
* Under construction

### External Plugins Example
* Under construction

## Where do I publish my mods?

The current default place is the [modding discord](https://discord.gg/hpAKq35FJf) in the mods channel, but this is subject to change.
