# Configure Form Definition JSON

A form definition JSON declares a custom form's identity, group and tier, behavior flags, body type, and state animations. Place it at:

`data/<namespace>/ssc_form/<form_name>.json`

This directory supports hot-reloading via `/reload`. Once loaded, test your form using `/shape_shifter_curse set_dynamic_form <player> <namespace>:<form_name>`.

---

## Full Example (1.10.0 Format)

```json
{
  "group": "example_namespace:example_group",
  "group_weight": 1,
  "tier": 1,
  "fallback": "shape-shifter-curse:allay_sp",
  "bodyType": "FERAL",
  "originID": "example_namespace:form_example",
  "originLayerID": "origins:origin",
  "eyeScale": 0.6,
  "flag": [
    "no_instinct",
    "no_cursed_moon_effect",
    "special_form"
  ],
  "anim": {
    "shape-shifter-curse:idle_state": {
      "controllerType": "shape-shifter-curse:sneak_anim_controller",
      "anim": { "animID": "example_namespace:form_example_idle" },
      "sneakAnim": { "animID": "shape-shifter-curse:form_feral_common_sneak_idle" }
    },
    "shape-shifter-curse:walk_state": {
      "controllerType": "shape-shifter-curse:sneak_anim_controller",
      "anim": { "animID": "shape-shifter-curse:form_feral_common_walk", "speed": 1.2, "fade": 2 },
      "sneakAnim": { "animID": "shape-shifter-curse:form_feral_common_sneak_walk" }
    },
    "shape-shifter-curse:jump_state": {
      "controllerType": "shape-shifter-curse:one_anim_controller",
      "anim": { "animID": "shape-shifter-curse:form_feral_common_jump" }
    }
  },
  "animDefault": {
    "controllerType": "shape-shifter-curse:sneak_anim_controller",
    "anim": { "animID": "example_namespace:form_example_idle" },
    "sneakAnim": { "animID": "shape-shifter-curse:form_feral_common_sneak_idle" }
  },
  "powerAnim": {
    "shape-shifter-curse:attach_side": {
      "animID": "shape-shifter-curse:bat_3_attach_side"
    }
  },
  "ExtraPower": [],
  "RemovedPower": [],
  "MasterForm": "shape-shifter-curse:feral_cat_sp",
  "PerkTree": "shape-shifter-curse:empty"
}
```

> For a full 13-state animation reference, see [example.json](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/custom_form_pack_example/example_form_datapack/data/example_namespace/ssc_form/example.json) in the repository.

---

## Core Fields

### Identity, Group & Tier

| Field | Description |
| --- | --- |
| `FormID` *(optional)* | Manually overrides the form ID. Usually omitted to default to `<namespace>:<filename>`. |
| `group` | Group ID (e.g., `example_namespace:my_wolf`). Forms in the same group advance and revert across tiers together. |
| `group_weight` | Selection weight within the same group and tier (usually `1`; set to `0` for forms like sub-forms that should not be picked randomly). |
| `tier` | Stage number (replaces legacy `groupIndex` and `phase`). `Phase Initial / Phase 1 / Phase 2 / Phase Permanent` map to `1 / 2 / 3 / 4`; Special Forms usually use `1` with the `special_form` flag. |
| `fallback` | Safe fallback form ID used automatically if the datapack is removed or the form becomes unavailable. |

### Appearance & Power Binding

| Field | Description |
| --- | --- |
| `bodyType` | `NORMAL` (humanoid) or `FERAL` (quadrupedal). Feral forms are recommended to reuse the built-in `form_feral_common_*` animations. |
| `originID` | Linked Origin ID; must be registered in `data/<namespace>/origins/` and `origin_layers/origin.json`. |
| `originLayerID` | Origin layer ID; keep `"origins:origin"` (not recommended to change). |
| `eyeScale` | Rendered eye height scale (actual hitbox scaling must still be set via a `shape-shifter-curse:scale` power). |
| `ExtraPower` / `RemovedPower` *(optional)* | Inline powers added directly to the form layer, or power IDs removed from the form. |
| `MasterForm` *(optional)* | Master form ID to register this form as a **Sub-Form** selectable via the `Ripple Mirror`. |
| `PerkTree` *(optional)* | Perk Tree ID attached to this form (omit or use `"shape-shifter-curse:empty"` if unused). |

### Behavior Flags (`flag`)

Version 1.10.0 uses the `flag` array to configure instinct, Cursed Moon, and inhibitor behavior:

- `special_form`: Marks a Special Form (for advancements and special-form logic).
- `no_instinct`: Hides the instinct bar and disables instinct gain (used for Special and Permanent Forms).
- `lock_instinct`: Locks the instinct bar display (used for `Phase 2`).
- `no_cursed_moon_effect` / `no_cursed_moon_tf_target`: Exempts the form from Cursed Moon effects or random Cursed Moon selection.
- `inhibitor_resist` / `inhibitor_immune`: Resists regular Inhibitors / blocks all non-creative Inhibitors (used for Permanent Forms).
- `initial_form`: Marks a `Phase Initial` form (allows reverting via Golden Apple).

---

## Animation Configuration (`anim` / `animDefault` / `powerAnim`)

Version 1.10.0 maps **FSM State IDs** to **Animation Controllers (`controllerType`)**:

- **`anim`**: Keys are state IDs under `shape-shifter-curse:` (`idle_state`, `walk_state`, `sprint_state`, `jump_state`, `fall_state`, `swim_state`, `climb_state`, `mining_state`, `attack_state`, `ride_state`, `sleep_state`, `fall_flying_state`, `flying_state`).
- **Common `controllerType` values**:
  - `shape-shifter-curse:one_anim_controller`: Single animation (`anim`).
  - `shape-shifter-curse:sneak_anim_controller`: Standing vs. sneaking (`anim`, `sneakAnim`).
  - `shape-shifter-curse:swim_anim_controller`: Floating vs. swimming (`anim`, `swimAnim`).
  - `shape-shifter-curse:ride_anim_controller`: Regular riding vs. vehicles (`anim`, `rideVehicleAnim`).
  - `shape-shifter-curse:use_other_state_anim_controller`: Reuses another state's controller (`StateControllerId`).
- **`animDefault`**: Fallback animation controller. Always configure this for `FERAL` forms so they do not revert to an upright pose.
- **`powerAnim`** *(optional)*: Override animations triggered by specific powers (such as `shape-shifter-curse:attach_side`).
