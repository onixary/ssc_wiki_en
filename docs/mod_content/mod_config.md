# Mod Configuration Options

It is highly recommended that you install [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) to configure the mod

### Player Custom Configuration Options

Configuration file path: `config\shape-shifter-curse-client-custom.toml`

- `keep_original_skin = true`

        Whether to keep your original skin

- `enable_form_color = true`

        Whether to enable form color customization feature

- `primaryColor = 13822450`

        Primary color of the form
        The value of this color is the decimal value converted from hexadecimal color
        It is recommended to install ModMenu to directly configure Hex colors intuitively in the game

- `accentColor1Color = 8967367`

        Accent color 1 of the form

- `accentColor2Color = 7829367`

        Accent color 2 of the form

- `eyeColor = 1118481`

        Eye color of the form. Only takes effect on forms where eye color is overridden

- `primaryGreyReverse = false`

        Whether to reverse the grayscale value of the primary color
        The custom colors of forms will be mixed with the grayscale texture of the original texture to achieve a more natural effect

- `accent1GreyReverse = false`

        Whether to reverse the grayscale value of accent color 1

- `accent2GreyReverse = false`

        Whether to reverse the grayscale value of accent color 2

### Client-Side Configurations

Configuration file path: `config\shape-shifter-curse-client.toml`

- `enableFormModelOnVanillaFirstPersonRender = true`
      
      Determines whether to render arm models of different forms in vanilla first-person view

      If experiencing frame drops in first-person view, recommended to set to false

- `newStartBookForBiggerScreen = false`
      
      Whether to enable the enlarged version of the Book of Shape Shifter pages

      Recommended to set to true when playing on high-resolution displays where UI appears too small

### Server-Side Common Configurations

Configuration file path: `config\shape-shifter-curse-common.toml`

- `transformativeBatSpawnChance = 0.5`
      
      Sets the spawn probability of Cursed Bats

- `transformativeAxolotlSpawnChance = 1.0`
      
      Sets the spawn probability of Cursed Axolotls

- `transformativeOcelotSpawnChance = 0.67`
      
      Sets the spawn probability of Cursed Ocelots

- `enableNewStartBook = true`
      
      Whether to enable the new version of the Book of Shape Shifter pages

      Enabled by default. Set to false to use the legacy version of the book pages
      
      Note: Legacy version requires owo-lib mod to function properly

- `curseMoonPhase = [1, 5]`

      Configure the moon phases when the Cursed Moon event takes effect, with a value range of 0-7. Default value is moon phase 1 and moon phase 5.

      When the values in the array are cleared, i.e., configured as "curseMoonPhase = []", the Cursed Moon event will be disabled.
      
      This is useful for creating modpacks that focus on a specific form.