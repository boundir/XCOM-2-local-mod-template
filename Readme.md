# XCOM 2 local mod template

- [XCOM 2 local mod template](#xcom-2-local-mod-template)
  - [Usage](#usage)
  - [Configuration](#configuration)
        - [Example](#example)
  - [Localization](#localization)
        - [Supported Languages:](#supported-languages)
  - [Resourses](#resourses)

## Usage

Download the template from [release][X2LocalModTemplate]
Place the mod in a folder configured in the [Alternative Mod Launcher][AML] (find how in the launcher wiki).

## Configuration

Inside the `Config` folder you can put base game or modded configuration files you want to modify. It can contain folders in case you want to organize your changes. Additionally the same file name can be found in different places.

```
├── Config
│   ├── Cosmetics
│   │   ├── XComContent.ini
│   ├── Framework
│   │   ├── AbilityEditor.ini
│   │   ├── XComRedefineUnits.ini
│   │   ├── XComTemplateCreator.ini
│   │   ├── XComTemplateEditor.ini
│   ├── Gameplay
│   │   ├── Loot
│   │   │   ├── XComGameCore.ini
│   │   ├── EnemyRebalance
│   │   │   ├── EnemyStats
│   │   │   │   ├── XComGameData_CharacterStats.ini
│   │   │   ├── EnemySkills
│   │   │   │   ├── XComGameData_SoldierSkills.ini
│   │   │   │   ├── XComGameCore.ini
│   ├── Misc
│   │   ├── XComInput.ini
│   ├── Missions
│   │   ├── XComEncounterLists.ini
│   │   ├── XComMissions.ini
```

##### Example

We want the **Chosen Assassin to have 100 aim with its sword** and we wish to **modify the upgrades for te Arashi** (Chosen shotgun).
Create the file `XComGameData_WeaponData.ini` in the `Config` folder.

```ini
[XComGame.X2Item_XpackWeapons]
; -CHOSENSWORD_CONVENTIONAL_AIM = 20
; -CHOSENSWORD_MAGNETIC_AIM = 20
; -CHOSENSWORD_BEAM_AIM = 20
; -CHOSENSWORD_T4_AIM = 20

CHOSENSWORD_CONVENTIONAL_AIM = 100
CHOSENSWORD_MAGNETIC_AIM = 100
CHOSENSWORD_BEAM_AIM = 100
CHOSENSWORD_T4_AIM = 100

!ChosenShotgunUpgrades=()

+ChosenShotgunUpgrades="CritUpgrade_Sup"
+ChosenShotgunUpgrades="ClipSizeUpgrade_Sup"
+ChosenShotgunUpgrades="FreeFireUpgrade_Sup"
+ChosenShotgunUpgrades="FreeKillUpgrade_Sup"
```

- `;` is a comment. It will not be used by the game.
- `-` is used to remove the previous value. As stated in [the Unreal Engine documentation][UDKConfigDoc] it has to be the exact copy of the previously set value for it to be removed.
Note that it is only necessary if you want to remove from a array. For numbers or strings it can be used as reference of the original value.
- `!` is used to empty an array.
- `+` is used to add to an array.


## Localization

Inside the `Localization` folder you can modify existing text or, if mods allow you to create things (unit, item, mission, ability), create your own localization. It works the same as the [`Config`](#configuration) folder and can have a similar folder architecture.

```
├── Localization
│   ├── BaseGameOverride
│   │   ├── XComGame.int
│   │   ├── XComGame.fra
│   ├── ModOverride
│   │   ├── XComGame.int
│   │   ├── XComGame.kor
│   ├── XComGame.chn
│   ├── XComGame.cht
│   ├── XComGame.deu
│   ├── XComGame.esn
│   ├── XComGame.fra
│   ├── XComGame.int
│   ├── XComGame.ita
│   ├── XComGame.jpn
│   ├── XComGame.kor
│   ├── XComGame.pol
│   ├── XComGame.rus
```

The **int** extension stands for international (english). If you're working on extending the text for a different language you need to modify the file with the corresponding extension.
For reference here are the supported languages for XCOM 2 based on the [Steam page][XCOM2SteamPage]:

##### Supported Languages:

| Language              | Extension         |
|---------------------  |----------------   |
| English               | int               |
| French                | fra               |
| Italian               | ita               |
| German                | deu               |
| Spanish - Spain       | esn               |
| Japanese              | jpn               |
| Korean                | kor               |
| Polish                | pol               |
| Russian               | rus               |
| Simplified Chinese    | chn               |
| Traditional Chinese   | cht               |

## Resourses

[Unreal Engine: Configuration Files][UDKConfigDoc] - *unreal engine website*
[Reddit: Configuration Files](https://www.reddit.com/r/xcom2mods/wiki/wotc_modding/config_files/) - *Reddit*
[Robojumper Blog: Configuration Files](https://robojumper.github.io/too-real/load-order/) *Robojumper's blog*
[Steam Guide: How to Preserve Mods' Configurations in a Local Mod](https://steamcommunity.com/sharedfiles/filedetails/?id=2820842366) - *Steam*

[AML]: https://github.com/X2CommunityCore/xcom2-launcher
[X2LocalModTemplateRelease]: https://github.com/boundir/X2LocalModTemplate/release/latest
[UDKConfigDoc]: https://docs.unrealengine.com/udk/Three/ConfigurationFiles.html
[XCOM2SteamPage]: https://store.steampowered.com/app/268500/XCOM_2/