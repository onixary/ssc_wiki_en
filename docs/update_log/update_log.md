# Update Log

### 1.0.0 - 1.0.2  
Initial version release and subsequent bug fixes.

### 1.0.31 - 1.0.32  
image  
Introduced the first quadrupedal form: feral_cat_sp.  
Resolved various issues related to quadrupedal forms, implementing a complete set of animations with corresponding first-person and third-person item perspectives.  
Added placeholder quadrupedal form phi_sp for customization purposes.  
Relevant bug fixes implemented.

### 1.0.4 - 1.0.41  
image  
Added new familiar_fox form.  
Implemented permanent form mechanics along with two new permanent forms: familiar_fox_3 and ocelot_3.  
Relevant bug fixes applied.

### 1.0.5  
**Server Compatibility Achieved**  
Special thanks to GitHub user [solunareclipse1](https://github.com/solunareclipse1) for providing key insights. After development efforts, the mod should now function correctly on servers.  

Note: Testing has only occurred in development environments, not actual server deployments. We recommend against installing this on primary servers until further verification.

**Important: Manual Save Migration Required**  
To accommodate server compatibility, this version moves save files from previous non-standard locations to development-conventional paths. To preserve your mod progress, manual migration is required:  

1. Locate old save location:  
`(MINECRAFT_VERSION)/Config/shape_shifter_curse_fabric/(WORLD_NAME)`  
You'll find multiple files beginning with your UUID. Copy these files.  
Cursed Moon event data requires no migration.  

2. Transfer to new save location:  
`(MINECRAFT_VERSION)/saves/(WORLD_NAME)/data/shape-shifter-curse`  
If the shape-shifter-curse folder doesn't exist, create it and paste your copied files.  
Migration is now complete.  

**Bug Fixes**  
- Resolved mob aggression issues with familiar_fox form  
- Fixed occasional display of player arm models in feral forms  

**Form Mechanism Improvements**  
- Axolotl mechanics optimized based on player feedback for improved engagement  
- Adjusted instinct triggers for several forms to create more natural progression

### 1\.0.51

Now (theoretically) compatible with Geckolib mod

Fixed Cursed Moon event frequency - enforced minimum 2-day interval between triggers

Removed false "Origins mod required" server join prompt

ocelot_2/3 evasion: Extended to all projectiles (was arrows only)

familiar_fox_1: Added missing cooldown to Energy Drain power

### 1\.0.52

Players forms can now correctly determine the edibility of food types from the Farmer's Delight mod

Fixed an issue where the Traveler's Backpack would disappear when placed on the ground in certain forms

Fixed cases where transformative mobs would replace original mobs

Limited the degree of FOV distortion caused by speed modifications to optimize the experience

The ocelot_2/ocelot_3 forms can now sweeping with bare-paw attacks

To ensure server compatibility, the mandatory dependency on the FirstPerson mod has been removed. It is no longer required to install the FirstPerson mod alongside the server installation

### 1\.0.53

Critical Fix: Resolved a bug where certain edible foods would fail to function properly when the Farmer's Delight mod was not installed

New Feature: familiar_fox 2/3 can now use empty bottles on Villagers / Illagers / Witches to craft Satiety Potions, improving survival gameplay in mob-scarce environments

Balance Adjustment: Instinct now gradually increases when the transformed form is within its preferred biome

### 1\.0.6

This update introduces a four-stage Snow Fox Progressive Form and one Permanent Bat Form.

Snow Fox Form:
This form is a variant of the Familiar Fox, representing a more "pure" version of the fox form.
You cannot brew this form’s potion directly. Instead, collect the Familiar Fox Potion (dropped occasionally by witches) and purify it in a brewing stand using a gold nugget.
"Leaping" is the core mechanic of this form.

Permanent Bat Form:
The fourth stage of the Bat Form
New mechanics include clinging and hanging upside-down—making it even more batty.

Additionally, several bug fixes and mechanic optimizations have been implemented.

### 1\.0.62

Thanks to the generous contributions of GitHub contributor [@xu233333](https://github.com/xu233333), this minor update delivers significant experience improvements.

- Fixed a bug where tipped arrows brewed from modded potions failed to take effect.

- Completed vanilla first-person adaptation. Form models now display correctly without requiring the FirstPerson mod (though we still recommend FirstPerson mod for enhanced immersion).

- Refactored the Shapeshifter's Guidebook UI logic using vanilla APIs, removing internal dependencies on owo-lib for better compatibility.

- Spawn probabilities for Cursed Creatures are now configurable. See [wiki](https://ssc-wiki.readthedocs.io/en/latest/mod_content/mod_config/) for details.

- Added missing descriptions for the \`snow_fox\` form.

### 1.0.63 - 1.0.64

- Fixed issue which bat_3's clinging/hanging animations not sync properly in multiplayer servers

- Powerful Inhibitor now correctly affects special forms

- [@xu233333](https://github.com/xu233333): add back detail screen for bigger text in Book of Shape Shifter

- Emergency fix issue which localization would fail when the owo-lib mod was not installed

### 1.0.7

The New Permanent Axolotl Form Is Here!

**Important Note:** Due to rewriting the form-related code logic, updating to version 1.0.7 **will reset players' current forms!**

Refer to wiki for instructions on using commands to restore previous forms. Alternatively, you can use an NBT editor to modify the corresponding fields in player save files to set forms.

- Permanent stage 4 axolotl form

  Unlike the stage 3, in the permanent form, your moisture (oxygen bar) will serve as a resource pool for releasing special water-flow abilities.

  Originally planned for release alongside the new wolf form, since some players wanted to experience it sooner, we decided to release a update for it.

- Cursed Moon phases is configurable now:
  
  You can now customize the moon phases that trigger the Cursed Moon event in the shape-shifter-curse-common.toml file or in-game settings. Changes require restarting the game/server to take effect.

  Clearing the moon phase array will disable the Cursed Moon event.

  Additionally, the default Cursed Moon frequency has been reduced to \[1, 5\] for a better experience.

- Colored text compatibility

  You can install [Rich Translatable Text](https://www.curseforge.com/minecraft/mc-mods/rich-translatable-text) mod to display colored text.

- Other Bug Fixes and Mechanic Optimizations

  Improved climbing animations for specific forms.

  Added support for datapacks to customize maximum potion stack sizes.

  Fixed conflicts with ExpandAbility.

### 1.0.71 & 1.0.72

Form Color Customization, Form Armor, and the New Custom Form System

- Form Color Customization System Added

    You can now customize your form colors and eye colors by using the ModMenu configuration or directly modifying the config\shape-shifter-curse-client-custom.toml configuration file.

    Configurable colors are divided into Primary Color, Accent Color 1, Accent Color 2 and Eye Color, allowing for flexible combinations.

- New Morphscale Armor

    A new type of armor called Morphscale Armor has been introduced, which can be equipped by most forms.

    To craft Morphscale Armor, you’ll need Untreated Moondust, Gold Ingots, Amethyst Shards, and the corresponding Diamond Armor. For details, please refer to the wiki.

- Completely Revamped Custom Form System

    The Custom Form System has been upgraded.

    Now, you can fully customize new form models, form powers, and state animations using data packs + resource packs, without being restricted by the previous empty forms.

    Refer to the wiki for more details.
