The mod uses [Origins](https://modrinth.com/mod/origins) logic to define different abilities for various forms. In other words, each form corresponds to a separate origin in Origins.

To define abilities for custom forms, please refer to the [Origins documentation](https://origins.readthedocs.io/en/latest/).

Additionally, the mod includes some extra powers and actions related to its unique mechanics.

---

## Additional Powers and Actions Added by the Mod:

### Instinct Value Related

These powers and actions interact with the instinct system to increase or decrease instinct values. Specific values are determined by predefined enums.

```json
{
    // Immediate effects (value type)
    FORM_OCELOT_ATTACK_LIVESTOCK(3.0f),
    // Effects for custom forms
    FORM_INSTANT_INSTINCT_MEDIUM(3.0f),
    FORM_INSTANT_INSTINCT_LARGE(5.0f),
    // Sustained effects (rate type)
    // Both catalyst and golden apple effects last 2 seconds
    FORM_USE_GOLDEN_APPLE(-4.25f / 2),
    FORM_USE_CATALYST(1.25f / 2),
    FORM_BAT_IN_DARK(0.004f),
    FORM_BAT_EAT_FRUIT(0.1f),
    FORM_BAT_NEAR_DRIPSTONE(0.006f),
    FORM_AXOLOTL_IN_WATER(0.004f),
    FORM_AXOLOTL_EAT_FISH(0.1f),
    FORM_AXOLOTL_NEAR_DRIPLEAF(0.008f),
    FORM_OCELOT_EAT_RAW_MEAT(0.1f),
    FORM_OCELOT_ON_LEAF(0.008f),
    // Effects for custom forms
    FORM_SUSTAINED_INSTINCT_ENVIRONMENT_MEDIUM(0.004f),
    FORM_SUSTAINED_INSTINCT_ENVIRONMENT_LARGE(0.008f),
    FORM_SUSTAINED_INSTINCT_FOOD(0.1f);
}
```

#### add_sustained_instinct_in_time
      
A power that increases or decreases instinct over a period of time, example below:

```json
   {
      "type": "origins:add_sustained_instinct_in_time",
      "instinct_effect_type": "FORM_AXOLOTL_EAT_FISH",
      "duration": 20,
      "is_on_item_finished": true,
      "condition": {
         "type": "origins:using_item",
         "item_condition": {
            "type": "origins:ingredient",
            "ingredient": {
               "tag": "origins:fish"
            }
         }
      }
   }
```

#### add_instinct
      
An action that instantly increases or decreases instinct, only applicable to enum definitions of immediate effects, example below:

```json
   {
      "type": "origins:self_action_on_hit",
      "entity_action": {
      "type": "origins:add_instinct",
         "instinct_effect_type": "FORM_OCELOT_ATTACK_LIVESTOCK"
      },
      "target_condition": {
         "type": "origins:in_tag",
         "tag": "origins:livestock"
      }
   }
```

Generally, for stages 0 and 1 of "Progressive Forms", it's necessary to define `add_sustained_instinct_in_time` powers for golden apples and catalysts. Of course, you can freely define your own instinct items.
   
---

### Character Scaling Related:
   
You can adjust character size scaling using the `scale` power. This scaling doesn't affect movement speed or jump height.

Every form **must** include a `scale` power, otherwise size irregularities may occur during form changes.

```json
{
   "type": "origins:scale",
   "scale" : 1.0
}
```

---

### Levitation Ability:
   
A power that grants the ability to fly to a certain height and hover in air when holding the jump key. The `"continuous"` value must be `true`.

```json
{
   "type": "origins:levitate",
   "ascent_speed": 0.3,
   "max_ascend_duration" : 30,
   "key": {
      "key": "key.jump",
      "continuous": true
   }
}
```
