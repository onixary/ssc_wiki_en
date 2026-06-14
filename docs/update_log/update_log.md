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

### 1.0.73

**Ocelot Form Mechanic Improvements**

Compared to other forms, the ocelot form's mechanics were somewhat simplistic. This update introduces new features:

- Ocelot_2 & Ocelot_3: Sneak rush now allows stepping over 1-block-high obstacles.

- Ocelot_3: You can now deal pounce damage by colliding with enemies mid-leap.

**Modified** Morphscale **Armor Crafting**

To craft Morphscale Armor now, you must first craft a Morphscale Core, then use the corresponding diamond gear, the Morphscale Core, and Untreated Moondust in a Smithing Table. This preserves the original equipment's enchantments.

Check the [wiki](https://ssc-wiki.readthedocs.io/en/latest/mod_content/morphscale_armors/) for details.

**Custom Color Optimization**

Color values now include an additional alpha channel. Setting it to 00 retains the vanilla texture color.

This is useful for modifying only specific parts (e.g., eye color).

Check the [wiki ](https://ssc-wiki.readthedocs.io/en/latest/mod_content/mod_config/)for details.

**Bug Fixes**

- Fixed Axolotl_3 appearing upside-down while crawling.

- Fixed Axolotl_3 launching attackers when wearing Thorns-enchanted armor while in Wave-Riding mode.

- Fixed localization errors in the Carnivore ability.

### **1\.0.74**

**Russian Localization**

Thanks to **[MaxMobile-ru](https://github.com/MaxMobile-ru)** for their contribution! The mod now includes **Russian translations**.

**Simplified Dependencies**

The mod now **only requires Azurelib, Pehkui** and **Satin-api** as a dependency.

**Minor Optimizations**

- **Morphscale Armor** has more defense now (see Wiki for details).

- **Heterochromia (different-colored eyes)** can now be configured in the **custom color settings**.

- Added **compatibility** with edible items from *Farmer's Delight, Ocean's Delight, Nether's Delight and Tide*

- **Allay_SP** can now **take off mid-air**, **walk on powder snow,** and gain some **saturation** when consuming **amethyst shards**.

- **Mophscale Core** and **Book of Shape Shifter** textures have been optimized.

**Bug Fixes**

- Fixed **edibility issues** with *Farmer's Delight* items.

- Fixed abnormal **riding animations** for some forms.

- Fixed **water speed limits** and **Depth Strider enchantment** not working properly for certain forms.

- Fixed **glowing effects** not displaying correctly on form models.

- Fixed **Allay_SP's levitate ability** behaving abnormally on servers.

### 1.0.76

This version fixes a critical bug that caused crashes and is recommended to update.

**Bug Fixes:**

- Fixed a critical bug in version 1.0.75 that caused the game to crash when foxes eating food.
  
- Fixed the issue where the increased damage from the Ocelot's bare-handed attacks was incorrectly applied to projectiles.
  
- Fixed the problem with the position of riding animation for Feral forms displaying incorrectly.

**Experience Improvements:**

- The water flow explosion power of Axolotl_3 no longer affects Item Frames.
  
- Familiar_fox no longer absorbs the energy of creatures while in sneaking.
  
- Familiar_fox no longer absorbs the energy of villagers and wandering merchants during transactions to optimize the trading experience. You will now need to hold an empty bottle to collect their energy.

### 1.8.0

The Wolf Form/Jackal Variant has been released!

**New Wolf Form:**

The Jackal Variant form has been introduced. This form focuses on group combat and it's "withering" power.

Search for the new entity called "Wandering Jackal Wraith" in the desert for transformation effect. 

**Experience Optimization:**

Unnecessary instinct bars are now hidden in permanent forms.

The mouth holding position of the Book of Shape Shifter in Feral Forms has been adjusted; it no longer gets stuck inside the player's head.

**Bug Fixes:**
- Fixed the issue where version 1.8.0-beta caused server crashes.
- Fixed the problem where the latest version of the FirstPerson mod affected the first-person perspective of certain forms.
- Fixed the bug where the final form of the Axolotl kept descending when viewed in Observer Mode.
- Fixed the issue where other players in the Feral Form could not properly display items they were holding in their mouths within the server environment.

### 1.8.1 - 1.8.2

This version reworks the mechanics of some weaker forms and introduces form-specific trinkets and tools to enrich the mod's gameplay experience.

1. Form Mechanic Changes

    1. Familiar Fox Form

       Hunger can now be restored normally through food, though with reduced efficiency.

       Additionally, an extra mana resource bar has been added for casting form abilities. The mana drain ability is now used to replenish the mana resource bar.

       Fire Arrow: Consumes a small amount of mana and uses a stick to fire a flaming arrow that ignites enemies. You can craft the advanced Fire Charm Paper item; consuming Fire Charm Paper lets you launch a more powerful fireball.

       Flame Ring: Consumes more mana. Press the ability key to cast a ring of fire that ignites and damages nearby targets.

       When your mana decreases, you will receive negative effects. At the permanent stage, when mana reaches zero, you will continuously take damage.

    2. Bat Form

       The permanent stage's clinging and hanging mechanics have been enhanced: the jump when leaving the clinging state is strengthened, allowing you to gain height through clinging.

       Its survivability has also been improved through exclusive trinkets and items.

    3. Axolotl Form

       The maximum health bonus while wet has been weakened, and Wave-Riding now slowly consumes wetness.

    4. Ocelot Form

       It can now automatically hiss to drive away phantoms.

2. Mechanic Optimizations

   Added an option to toggle random form sounds, as well as a key binding to actively play form sounds.

   For Ocelot Form, added a key binding to toggle sneak edge protection to improve control feel.

   Some forms' entity glow effects are now hidden when F1 is enabled, making screenshots easier.

   Reduced the movement speed and damage of wild Jackal Wraiths.

3. Exclusive Trinkets and Tools

   Please see the mod wiki page.

4. Bug Fixes

   Fixed a bug where jumping on a bed during the transformation animation would launch you into the air.

### 1.8.3

1. Merged the Russian localization made by [MaxMobile-ru](https://github.com/MaxMobile-ru).

2. Added dietary compatibility for foods from several mods.

### 1.9.0-1.9.1

The new Spider Form is now available!

1. Spider Form

    Webbing is the core mechanic of Spider Form: fire web projectiles to build climbable cobweb structures and obstruct enemy movement. In later stages, the form also gains stronger mobility abilities.

    Spider Form also has an extra second-pair-of-hands trinket slot, allowing exclusive trinkets and tools to further enhance its abilities.

2. Mechanic Optimizations

    Added a compatibility layer for Trinkets and native Curios in the Sinytra Connector version, so form trinkets can now be placed directly into Curios slots.

    Entries in the Book of Shape Shifter now support automatically scrolling text, so overly long text will no longer be truncated.

    Added several vanilla-form achievements as in-game guidance.

    Added vanilla recipe unlocks for related items.

    Optimized the footsteps of Spider Form and Feral Form so they better match their four-legged movement pattern.

3. Bug Fixes

    Fixed missing sound effects and missing night vision for Spider Form, along with several related issues.

    Cursed Spiders now remain neutral under light, matching vanilla spiders.

    Fixed missing localization descriptions for some forms.

### 1.9.2

1. New visual and interactive form color menu

    The game now includes a brand-new visual and interactive color menu. You can precisely adjust form colors through RGB sliders and other controls while previewing the result in real time, so you no longer need to test Hex colors one by one.

    You can open the color menu from the new button added to the Book of Shape Shifter, or from the mod configuration menu (requires Mod Menu).

2. Merged the latest Russian localization made by [MaxMobile-ru](https://github.com/MaxMobile-ru). Many thanks!

3. Updated the mod wiki pages.
