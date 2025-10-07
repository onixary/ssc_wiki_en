# Package Structure Example

Please refer to the examples in the [GitHub repository](https://github.com/onixary/shape-shifter-curse-fabric/tree/master/custom_form_pack_example)

A custom form consists of two parts: a resource pack and a datapack. The resource pack is responsible for implementing form models and animations, while the datapack is responsible for defining form abilities, types, body types, etc.

For a complete custom form, both need to be loaded and applied simultaneously

## Resource Pack Structure

```
example_form_resourcepack // Resource pack root directory
├── assets 
│   ├── example_namespace // Namespace for custom forms. Always use your own namespace to prevent conflicts
│   │   ├── lang // Localization file directory
│   │   │   ├── en_us.json // English localization file
│   │   │   └── zh_cn.json // Chinese localization file
│   │   ├── rich_lang // Rich text localization file directory
│   │   │   ├── en_us.json // English localization file
│   │   │   └── zh_cn.json // Chinese localization file
│   │   └── player_animation // Custom animation file directory
│   │       └── form_example_idle.json // Custom animation file example, exported using AzureLib format
│   └── orif-defaults // Custom model and animation file directory, using OriginFur mod format
│       ├── furs // Custom form model JSON definition directory
│       │   └── example_namespace.form_example.json // JSON definition file for custom form model, including configurations for textures and soft bones
│       ├── geo // Custom form model directory
│       │   └── form_example.geo.json // Exported model file in AzureLib geo format
│       └── textures // Custom form model texture directory
│           └── form_example.png // Custom form model texture
└── pack.mcmeta // Package description file
```

## Datapack Structure

```
example_form_datapack // Datapack root directory
├── data
│   ├── example_namespace // Namespace for custom forms, consistent with the namespace in the resource pack
│   │   ├── origins // Origins' origin definition directory
│   │   │   └── form_example.json // Origin definition corresponding to custom form
│   │   ├── origins_power_extra // Directory for additional custom abilities to be mounted on existing forms
│   │   │   └── append_transform.json // JSON for additional abilities mounted on existing forms, needed to implement transformation triggers
│   │   ├── powers // Origins' powers custom ability directory
│   │   │   ├── custom_eat_amethyst_shard.json // Example of powers custom ability definition
│   │   │   └── custom_night_vision.json
│   │   └── ssc_form // Form definition JSON file directory
│   │       └── form_example.json // Custom form definition JSON file. Animations, form types, body types, etc. are all defined here
│   └── origins\origin_layers // origin_layers directory
│       └── origin.json // origin_layers registration file. Only by adding example_namespace:form_example in it can it be recognized by origins
└── pack.mcmeta // Package description file

```