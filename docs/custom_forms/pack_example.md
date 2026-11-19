# Resource Pack / Datapack Structure

Please refer to the [GitHub Repository Example](https://github.com/onixary/shape-shifter-curse-fabric/tree/master/custom_form_pack_example) alongside this page.

A complete custom form consists of two parts that must be loaded together:

- **Resource Pack**: Handles 3D models, textures, color masks, soft-bone/blinking configs, player animations, and localization text.
- **Datapack**: Handles form definitions (groups, tiers, flags, animation bindings), powers, transformation triggers, trinket effects, and potion recipes.

Always use your own unique namespace (`example_namespace` below) to avoid conflicts.

---

## Resource Pack Structure (1.10.0)

Starting from 1.10.0, model configs and assets are placed inside your own namespace instead of `assets/orif-defaults/furs/`:

```text
example_form_resourcepack/
├── pack.mcmeta
└── assets/
    └── example_namespace/
        ├── geo/                          # .geo.json models exported with GeckoLib
        │   └── form_example.geo.json
        ├── textures/                     # Form textures, colormasks, and emissive textures
        │   └── form_example.png
        ├── ssc_form_model/               # Form model config JSONs (replaces orif-defaults/furs)
        │   └── origins.origin.example_namespace.form_example.json
        ├── player_animation/             # Player animation JSONs exported with GeckoLib
        │   └── form_example_idle.json
        ├── lang/                         # Plain-text localization files
        │   ├── en_us.json
        │   └── zh_cn.json
        └── rich_lang/                    # Optional: colored rich-text localization files
            ├── en_us.json
            └── zh_cn.json
```

---

## Datapack Structure (1.10.0)

```text
example_form_datapack/
├── pack.mcmeta
└── data/
    ├── example_namespace/
    │   ├── ssc_form/                     # Core form definition JSONs (supports /reload)
    │   │   └── example.json
    │   ├── origins/                      # Origin definitions for your forms
    │   │   └── form_example.json
    │   ├── powers/                       # Custom powers (Apoli / SSC custom powers)
    │   │   ├── custom_scale.json
    │   │   ├── custom_night_vision.json
    │   │   ├── to_example_form.json
    │   │   └── to_example_form_by_effect.json
    │   ├── origins_power_extra/          # Optional: attach extra powers to existing forms
    │   │   └── append_transform.json
    │   ├── accessory_power/              # Optional: custom trinket powers for forms
    │   │   └── example.json
    │   ├── dynamic_brewing_recipes/      # Optional: custom form potion brewing recipes
    │   │   └── example_potion_recipe.json
    │   └── tags/                         # Optional: custom entity/item tags
    │       └── entity_types/
    │           └── attack_to_example_effect_entity.json
    └── origins/
        └── origin_layers/
            └── origin.json               # Register your custom Origin (example_namespace:form_example) here
```
