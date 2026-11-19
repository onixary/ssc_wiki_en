# Adding Custom Form Models and Animations

Both custom form models and animations are created with [Blockbench](https://www.blockbench.net/).

Starting from version 1.10.0, runtime rendering migrated to **GeckoLib 4.x**, so both models and animations should now be exported using Blockbench's **`GeckoLib Animation Utils`** plugin.

---

## Important: Differences Between Model Projects and Animation Projects

Form models follow the Origin Furs bone hierarchy, while player animations are based on [playerAnimator](https://modrinth.com/mod/playeranimator). Because the two formats differ, **do not mix them**:

1. **Opposite Facing Axis**: Form models face **+Z**, whereas animation models face **-Z**.
2. **Swapped Leg Bone Names**: Left and right leg bone names in form models are swapped (a legacy quirk from Origin Furs). Keep them as-is so legs render properly.

It is strongly recommended to start from the repository's [form model template](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/3d_models/player_form/axolotl/form_axolotl_2.bbmodel) and [feral animation template](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/3d_models/player_form/0_common/feral_form/animation/form_feral_common_anim.bbmodel).

---

## 1. Configuring Custom Models (`ssc_form_model`)

1. Export your `.geo.json` model with the GeckoLib plugin and place it in `assets/<namespace>/geo/`.
2. Place your textures in `assets/<namespace>/textures/`.
3. Create a model config JSON under `assets/<namespace>/ssc_form_model/` (replacing the legacy `assets/orif-defaults/furs/` directory), named `origins.origin.<namespace>.<origin_name>.json`.

### Model Config Example (1.10.0 Format)

```json
{
  "load_priority": 0,
  "name": "example_namespace.form_example.model_name",
  "layer": "origins:origin",
  "form": "example_namespace:form_example",
  "wide_only": true,

  "model": "example_namespace:geo/form_example.geo.json",
  "texture": "example_namespace:textures/form_example.png",
  "hidden": [
    "leftLeg", "rightLeg", "rightPants", "leftPants",
    "leftSleeve", "rightSleeve", "leftArm", "rightArm",
    "body", "jacket", "head", "hat"
  ],

  "animation_system": "shape-shifter-curse:default",
  "animation_system_config": {
    "tail": {
      "chain": {
        "tail": [0, 1, 2, 3]
      }
    },
    "head_tail": {
      "chain": {
        "ear_l": [0],
        "ear_r": [0]
      }
    },
    "wing_l": {
      "chain": {
        "wing_l": [0, 1]
      }
    },
    "wing_r": {
      "chain": {
        "wing_r": [0, 1]
      }
    },
    "eye_blink": {
      "eye": "eyeRoot",
      "open_scale": 1.0,
      "close_scale": 0.01
    }
  }
}
```

### Key Fields

- **`layer` / `form`**: Matches the datapack Origin layer (`origins:origin`) and Origin ID (`example_namespace:form_example`).
- **`hidden`**: Vanilla player model parts to hide.
- **`animation_system` & `animation_system_config`** (new in 1.10.0):
  - `tail`: Soft-bone chains parented to the torso (tails, ribbons).
  - `head_tail`: Soft-bone chains parented to the head (ears, tufts).
  - `wing_l` / `wing_r`: Left and right wing bone chains.
  - `eye_blink`: Automatic eye-blinking config; add an `eyeRoot` bone under `bipedHead` in your model.
  - Ensure all bones in a chain share a consistent naming prefix (e.g., `tail_0`, `tail_1`, `tail_2`).

!!! note

    **Migration Notice**: Legacy top-level `tail_chain`, `wing_chain_l`, and `builtin_controller_data` fields from 1.9.2 and earlier are **no longer read in 1.10.0** (tails and wings will silently stop animating). Migrate them to `animation_system` + `animation_system_config`.

---

## 2. Adding Custom Player Animations

1. Install the **GeckoLib** plugin in Blockbench, open an [existing animation template](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/3d_models/player_form/0_common/feral_form/animation/form_feral_common_anim.bbmodel), author your keyframe animations in the `Animate` tab, and export.
2. Place exported animation JSON files in `assets/<namespace>/player_animation/`.
3. Reference the animation IDs inside `anim`, `animDefault`, or `powerAnim` of your form definition JSON (`ssc_form/*.json`).

Reuse the mod's built-in animations (such as `shape-shifter-curse:form_feral_common_*`) whenever possible and only author custom animations where needed.
