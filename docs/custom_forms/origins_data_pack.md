# Adding Custom Form Powers

The mod defines form abilities using the Apoli / Origins power system—each form corresponds to an Origin defined under `data/<namespace>/origins/` and registered in `data/origins/origin_layers/origin.json`.

For general power syntax, please refer to the [Origins Documentation](https://origins.readthedocs.io/en/latest/).

!!! note

    **1.10.0 Namespace Migration Tips:**
    - Use the `apoli:` prefix for Power, Action, and Condition types (`origins:` types remain compatible for now, though future versions plan to phase them out).
    - Diet, weapon, and block tags (such as `fish`, `meat`, `raw_meat`, and `ignore_diet`) have migrated to the **`shape-shifter-curse:`** namespace (e.g., `shape-shifter-curse:fish`).

---

## 1. Adding Transformation Entry Points

You can let players enter your custom form in survival through any combination of the following methods:

### 1. Attach Transformation Trigger Powers (`origins_power_extra`)

Create a JSON file under `data/<namespace>/origins_power_extra/` to attach extra powers to an existing form (such as the default post-book form `shape-shifter-curse:form_original_shifter`):

```json
{
  "TargetLayerID": "origins:origin",
  "TargetOriginsID": "shape-shifter-curse:form_original_shifter",
  "ExtraPowers": [
    "example_namespace:to_example_form",
    "example_namespace:to_example_form_by_effect"
  ]
}
```

Then implement the trigger power in `data/<namespace>/powers/`. For example, use `shape-shifter-curse:transform_to_form` for direct transformation:

```json
{
  "type": "apoli:action_on_item_use",
  "entity_action": {
    "type": "shape-shifter-curse:transform_to_form",
    "form_id": "example_namespace:example",
    "instant": true
  },
  "item_condition": {
    "type": "apoli:ingredient",
    "ingredient": {
      "tag": "shape-shifter-curse:fish"
    }
  }
}
```

Or use `shape-shifter-curse:give_custom_transform_effect` to apply a custom transformation status effect (triggering transformation the next time the player sleeps):

```json
{
  "type": "apoli:self_action_when_hit",
  "entity_action": {
    "type": "shape-shifter-curse:give_custom_transform_effect",
    "form_id": "example_namespace:example"
  },
  "damage_condition": {
    "type": "apoli:attacker",
    "entity_condition": {
      "type": "apoli:in_tag",
      "tag": "example_namespace:attack_to_example_effect_entity"
    }
  }
}
```

### 2. Add a Custom Form Potion (`dynamic_brewing_recipes`)

Create a JSON file under `data/<namespace>/dynamic_brewing_recipes/` to register a brewing stand recipe for your form:

```json
{
  "type": "potion",
  "input": "shape-shifter-curse:moondust_potion",
  "ingredient": "minecraft:bone",
  "output": "shape-shifter-curse:to_custom_statue_potion",
  "target_form": "example_namespace:example"
}
```

### 3. Custom Trinket Effects (`accessory_power`)

Create a JSON file under `data/<namespace>/accessory_power/` to add or remove powers when specific trinkets are equipped in your custom form (see [accessory_power/example.json](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/custom_form_pack_example/example_form_datapack/data/example_namespace/accessory_power/example.json) in the repository).

---

## 2. Common Mod-Specific Powers and Actions

### 1. Instinct System

#### `add_sustained_instinct` (Continuous Instinct Change)

If two powers share the same `instinct_effect_id`, the later one overrides the earlier one. Example adding +0.003 instinct per tick while in Lush Caves:

```json
{
  "type": "shape-shifter-curse:add_sustained_instinct",
  "instinct_effect_id": "FORM_AXOLOTL_BIOME",
  "value": 0.003,
  "duration": 1,
  "condition": {
    "type": "apoli:biome",
    "biome": "minecraft:lush_caves"
  }
}
```

#### `add_instinct` (One-Time Instinct Action)

Example adding +0.1 instinct per tick for 20 ticks (+2 total) when eating fish:

```json
{
  "type": "apoli:action_on_item_use",
  "entity_action": {
    "type": "shape-shifter-curse:add_instinct",
    "instinct_effect_id": "FORM_AXOLOTL_EAT_FISH",
    "value": 0.1,
    "duration": 20
  },
  "item_condition": {
    "type": "apoli:ingredient",
    "ingredient": {
      "tag": "shape-shifter-curse:fish"
    }
  }
}
```

For `Phase Initial` and `Phase 1` of progressive forms, consider reusing the built-in [Golden Apple](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/src/main/resources/data/shape-shifter-curse/powers/form_instinct_use_golden_apple.json) and [Catalyst](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/src/main/resources/data/shape-shifter-curse/powers/form_instinct_use_catalyst.json) instinct powers.

### 2. Player Scaling (`scale`)

Dynamic datapack forms require `shape-shifter-curse:scale` to control hitbox scale (without altering movement speed or jump height), paired with `eyeScale` in `ssc_form/*.json`:

```json
{
  "type": "shape-shifter-curse:scale",
  "scale": 0.55,
  "eye_scale": 0.6
}
```

### 3. Additional Custom Powers and Actions

All custom powers, actions, and conditions added by the mod (including active skill keys `key.shape-shifter-curse.active_skill_1`–`_6`) can be browsed in the [additional_power](https://github.com/onixary/shape-shifter-curse-fabric/tree/master/src/main/java/net/onixary/shapeShifterCurseFabric/additional_power) directory of the source repository.
