# Adding Custom Form Models and Animations

## Important Note: Differences between Model Blockbench Projects and Animation Blockbench Projects

Custom animations and models both need to be created using [Blockbench](https://www.blockbench.net/)

Custom form models are based on the implementation of [Origin Furs](https://modrinth.com/mod/origin-furs), while form animations are based on the implementation of [playerAnimator](https://modrinth.com/mod/playeranimator)

The **facing direction** and **left/right naming** of the two models are different and cannot be mixed:

1. Form models face the +Z direction, while form animation models face the -Z direction

2. In form models, the naming of leg bones is **reversed left and right**. This may be a legacy issue with Origin Furs itself, and since fixing it would cause errors, please maintain the current naming

It is recommended that you implement your own form models and animations by modifying existing [form model projects](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/3d_models/player_form/axolotl/form_axolotl_2.bbmodel) and [form animation projects](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/3d_models/player_form/0_common/feral_form/animation/form_feral_common_anim.bbmodel)

## Adding Custom Models

The mod implements custom models for different forms based on the logic of [Origin Furs](https://modrinth.com/mod/origin-furs). Form models should be easily migratable from other Blockbench character models

To add custom models for specific forms, please refer to the [Origin Furs documentation](https://originalfur.readthedocs.io/en/latest/) and the Blockbench project files in the source code [player_form directory](https://github.com/onixary/shape-shifter-curse-fabric/tree/master/3d_models/player_form)

To export form models, you need to install the `AzureLib Animator` plugin in Blockbench and select `Export Azurelib.geo Model` when exporting

### Registering Model Textures and Soft Bones

The mod additionally implements soft bones for tails/ribbons and dynamic wings. These also need to be registered in the JSON file, as shown in the example below:

```json
{
  "model": "orif-defaults:geo/form_allay_sp.geo.json",
  "texture": "orif-defaults:textures/form_allay_sp/form_allay_sp.png",
  "overlay": "orif-defaults:textures/form_allay_sp/form_allay_sp_overlay.png",
  "hidden": [
    "leftLeg",
    "rightLeg",
    "rightPants",
    "leftPants",
    "body",
    "jacket"
  ],
  "tail_chain": {
    "tail_l": [0, 1, 2],
    "tail_r": [0, 1, 2]
  },
  "wing_chain_l": {
    "wing_l": [0, 1]
  },
  "wing_chain_r": {
    "wing_r": [0, 1]
  },
  "tail_chain_head": {
    "head_tail_l": [0, 1],
    "head_tail_r": [0, 1]
  }
}
```

`tail_chain`: Soft bone chain for tails/ribbons with trunk as parent

`tail_chain_head`: Soft bone chain for head attachments with head as parent

`wing_chain_l` and `wing_chain_r`: Bone chains for wings, differentiated by left and right

Ensure that all bone prefix names in a bone chain in Blockbench remain consistent

## Adding Custom Animations

## Note: The current Blockbench 5 version will break the animation export of the Azure Animation plugin, please use the BlockBench 4 version

The mod implements custom animations for different forms based on the method of [playerAnimator](https://modrinth.com/mod/playeranimator)

To add custom animations, you also need to install the `AzureLib Animator` plugin in Blockbench and refer to the [existing animation project](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/3d_models/player_form/0_common/feral_form/animation/form_feral_common_anim.bbmodel), creating frame animations in the `Animate` tab that appears in the upper right corner

Your animation JSON files should be placed under `assets/example_namespace/player_animation`

After creation and export, you also need to register in the [JSON configuration file](https://ssc-wiki.readthedocs.io/zh-cn/latest/custom_forms/form_definition_json/)

It is recommended that you first reuse animations already implemented in the mod, and only create your own when there is no suitable animation
