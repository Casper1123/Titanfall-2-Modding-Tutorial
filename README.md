# Titanfall 2 Modding Tutorial
This repository hosts files related to a simple modding tutorial for Titanfall 2. <BR> <BR>

The tutorial can be found [here](link here). <BR>
# These files depend on the following repositories: <BR>
- [Titanfall 2 Northstar Client](https://github.com/R2Northstar/Northstar) & [VanillaPlus](https://github.com/Zayveeo5e/NP.VanillaPlus) <BR> <BR>
# Other useful links: <BR>
- [NoSkill Crosshair Modding](https://noskill.gitbook.io/titanfall2/modding/weapon-config-info/crosshair-modding) - [Thunderstore Mod Page](https://thunderstore.io/c/northstar/)<BR><BR><BR>

# Usage: <BR>
- Install [Northstar](https://github.com/R2Northstar/Northstar). The tutorial uses the manual unzipping method.
- Install [VanillaPlus](https://github.com/Zayveeo5e/NP.VanillaPlus). The tutorial uses the manual unzipping method.
- Ensure that you do not have any of the default R2Northstar/mods installed; these must be removed.
- Go into your Launch Arguments and insert `-vanilla -northstar`.
- Launch the game. The main menu screen should have a slightly different logo.
- Close the game and install the mods and packages you'd like to install. For this repo, the two mods given go into the mods folder. For Thunderstore mods, put the downloaded files into packages.
# Modding text and crosshairs
## Text
- Go into the mod files.
- Navigate to `r1_lang.txt` where lang is your game language (so for my example, r1_english.txt).
- Edit the **right hand side** text. Do **NOT** edit the left hand side text. Search for the text you want to alter using for example [notepad++](https://notepad-plus-plus.org/) and save.
- With the mod installed, reload your mods or restart the game.
## Crosshairs
- Go into the mod files.
- Navigate to the weapon scripts folder.
- Find the weapon you are looking for. *If it does not exist, like the Laser Core (mp_titancore_lasercannon.txt), then feel free to create it yourself. Just paste the crosshair text in the file to make it work, but ensure it's encapsulated in a `WeaponData{ ... }`*
- Scroll to the bottom to find the crosshair data; see the following Alternator example;
```txt
active_crosshair_count				"1"
rui_crosshair_index					"0"

RUI_CrosshairData
{
	DefaultArgs
	{
		adjustedSpread				weapon_spread
		adsFrac 					player_zoomFrac
		isSprinting					player_is_sprinting
		isReloading					weapon_is_reloading
		teamColor					crosshair_team_color
		isAmped						weapon_is_amped
		crosshairMovementX          crosshair_movement_x
		crosshairMovementY          crosshair_movement_y
	}

	Crosshair_1
	{
		"ui"						"ui/crosshair_alternator"
		"base_spread"				"1.0"
		Args
		{
			isFiring				weapon_is_firing
		}
	}
}
```
We see that there is an active_crosshair_count, which you'll need to update if you add more crosshairs to the file. <BR>
Here is an example **complete** file for the Laser Shot (`mp_titanweapon_laser_lite.txt`) that adds a small dot to the center of the crosshair: <BR>
```txt
WeaponData
{
	active_crosshair_count				"2"

	RUI_CrosshairData
	{
		DefaultArgs
		{
			adjustedSpread				weapon_spread
			adsFrac 					player_zoomFrac
			isSprinting					player_is_sprinting
			isReloading					weapon_is_reloading
			teamColor					crosshair_team_color
			isAmped						weapon_is_amped
			crosshairMovementX          crosshair_movement_x
			crosshairMovementY          crosshair_movement_y
		}

		Crosshair_1
		{
			"ui"						"ui/crosshair_circle2_small"
			"base_spread"				"0.0"
			Args
			{
				isFiring				weapon_is_firing
			}
		}
		Crosshair_2
		{
			"ui"						"ui/crosshair_wingman_n"
			"base_spread"				"0"
			Args
			{
				isFiring				weapon_is_firing
			}
		}
	}
}
```
From this example as well as the [NoSkill Crosshair Modding page](https://noskill.gitbook.io/titanfall2/modding/weapon-config-info/crosshair-modding) you should be able to figure out how to add/change crosshairs. <BR>
Find information on the Args on the NoSkill wiki as well.