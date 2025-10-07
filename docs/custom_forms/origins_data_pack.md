# Adding Custom Form Abilities

The mod uses the logic of [Origins](https://modrinth.com/mod/origins) to define different abilities for different forms. In other words, each form corresponds to a separate origin in Origins

To define abilities for custom forms, please refer to the [Origins documentation](https://origins.readthedocs.io/en/latest/)

In addition, the mod has additionally added some powers and actions related to specific mechanisms for use

---

## Transformation Trigger Powers Mounted on Existing Forms

### Mounting Transformation Powers

To trigger transformation through in-game conditions, you first need to mount your own transformation power in the `custom_form_pack_example/example_form_datapack/data/example_namespace/origins_power_extra` directory

```
{
  "TargetOriginsID": "shape-shifter-curse:form_original_shifter",
  "ExtraPowers": [
    "example_namespace:to_example_form"
  ]
}
```

In the above example, the power `example_namespace:to_example_form` will be mounted under the form `shape-shifter-curse:form_original_shifter`

This way, when you are in the `form_original_shifter` form, you can trigger the transformation effect implemented in the power `to_example_form`

If you implement your own basic form instead of reusing the basic forms in the mod, you can skip the mounting step and directly implement the transformation power in your own basic form

### Implementation of Transformation Powers

After mounting in JSON, you need to implement your own transformation power

Like other powers, transformation powers need to be placed in the `custom_form_pack_example/example_form_datapack/data/example_namespace/powers` directory

You can find all current form IDs [here](https://github.com/onixary/shape-shifter-curse-fabric/tree/master/src/main/resources/data/shape-shifter-curse/origins)

Use the `shape-shifter-curse:transform_to_form` action to trigger the transformation logic:

```
{
  "type": "origins:action_on_item_use",
  "entity_action": {
    "type": "shape-shifter-curse:transform_to_form",
    "form_id": "example_namespace:example",
    "instant": true
  },
  "item_condition": {
    "type": "origins:ingredient",
    "ingredient": {
      "tag": "origins:fish"
    }
  }
}
```

In the above example, when a player eats any fish, `shape-shifter-curse:transform_to_form` will be triggered, transforming the player into the `example_namespace:example` form

Since you have registered the power to be mounted under the `form_original_shifter` form, this power will only take effect when in that form

---

## Mod-Specific Powers and Actions:

### Instinct System Related

These powers and actions are used to interact with the mod's instinct system, used to increase or decrease instinct values under specific conditions

#### add_sustained_instinct
      
Power used to continuously increase or decrease instinct

When the `instinct_effect_id` field of a power duplicates with an existing power, the later loaded power will overwrite the existing power

The following example implements continuously increasing instinct values at a rate of 0.003 per tick when the player is in the Lush Caves biome

```json
    {
      "type": "shape-shifter-curse:add_sustained_instinct",
      "instinct_effect_id": "FORM_AXOLOTL_BIOME",
      "value": 0.003,
      "duration": 1,
      "condition": {
        "type": "origins:biome",
        "biome": "minecraft:lush_caves"
      }
    }
```

#### add_instinct
      
Action to increase or decrease instinct once

The following example implements increasing instinct value by 0.1 per tick for 20 ticks each time a player eats raw fish. That is, increasing 2 instinct values within 1 second

```json
    {
      "type": "origins:action_on_item_use",
      "entity_action": {
        "type": "shape-shifter-curse:add_instinct",
        "instinct_effect_id": "FORM_AXOLOTL_EAT_FISH",
        "value": 0.1,
        "duration": 20
      },
      "item_condition": {
        "type": "origins:ingredient",
        "ingredient": {
          "tag": "origins:fish"
        }
      }
    }
```

Generally speaking, for the 0th and 1st stages of "phased transformation forms", it is necessary to include powers related to [golden apples](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/src/main/resources/data/shape-shifter-curse/powers/form_instinct_use_golden_apple.json) and [catalysts](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/src/main/resources/data/shape-shifter-curse/powers/form_instinct_use_catalyst.json). Of course, you can also freely define your own instinct items

---

### Character Scaling Related:
   
You can adjust character size scaling through the `scale` power, this scaling will not affect form movement speed, jump height, and other attributes

The `eye_scale` field is used to define camera height scaling
   
Each form **must** contain a `scale` power, otherwise size confusion may occur when transforming forms

```json
{
  "type": "shape-shifter-curse:scale",
  "scale": 0.5,
  "eye_scale": 0.6
}
```

---

### Other Specific Powers and Actions:
   
Custom powers, actions, and conditions used by various forms in the mod are all in the source code [additional_power](https://github.com/onixary/shape-shifter-curse-fabric/tree/master/src/main/java/net/onixary/shapeShifterCurseFabric/additional_power) directory, no further elaboration here

Feel free to refer to and reuse them