# Overview

Please start by checking the complete example datapack and resource pack in the [GitHub Repository](https://github.com/onixary/shape-shifter-curse-fabric/tree/master/custom_form_pack_example).

Starting from version 1.10.0, the mod's underlying form and model animation systems were rewritten. Using a **datapack** + **resource pack**, you can flexibly create custom forms, sub-forms, models and animations, powers, dynamic form potions, and trinket effects.

!!! note

    **Migration Notice for Pre-1.10.0 Pack Authors:**
    Version 1.10.0 introduced breaking format updates to form definition JSONs (`ssc_form`), model config paths (moved to `ssc_form_model`), soft-bone animation configs (moved to `animation_system`), and several tag namespaces. Legacy custom form packs must migrate following this section.

---

### What You Can Do with Resource Packs / Datapacks

- **Define Full Custom Forms or Sub-Forms**: Configure form groups, tiers, weights, body types (humanoid/feral), behavior flags, and fallback forms via `ssc_form`, register sub-forms via `MasterForm`, or attach a `PerkTree`.
- **Add Transformation Entry Points**: Attach transformation triggers via `origins_power_extra`, apply custom transformation status effects via `give_custom_transform_effect`, and register custom form brewing recipes via `dynamic_brewing_recipes`.
- **Customize Models & Animations**: Configure GeckoLib models, color masks, emissive textures, eye-blinking bones, and soft-bone chains via `ssc_form_model`, and bind `playerAnimator` state animations.
- **Customize Powers & Trinket Effects**: Write abilities with Apoli / Origins syntax, add or remove powers directly in form JSONs via `ExtraPower` / `RemovedPower`, and define form-specific trinket bonuses via `accessory_power`.
- **Custom Codex Text**: Customize form names, descriptions, pros, cons, and instinct entries in the Book of Shape Shifter via `lang` and `rich_lang`.

### Current Limitations

- Standalone custom transformative mob entities cannot be added through datapacks alone (however, you can grant custom transformation effects through powers listening to hit or interaction events).
- Dynamic datapack forms still require the `shape-shifter-curse:scale` power to control hitbox scaling (paired with `eyeScale` in the form JSON for rendered eye height).
