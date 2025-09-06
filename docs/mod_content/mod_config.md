# Mod Configuration Options

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
