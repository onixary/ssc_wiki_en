# Custom Models Using Origin Furs Data-Driven Approach

The mod implements custom models for different forms based on [Origin Furs](https://modrinth.com/mod/origin-furs) logic. Form models should be easily migratable from other Blockbench character models.

To add custom models for specific forms, please refer to the [Origin Furs documentation](https://originalfur.readthedocs.io/en/latest/) and the Blockbench project files in the `3d_models` directory of the source code.

!!! note

    To export form models, you need to install the `AzureLib Animator` plugin and select `Export Azurelib.geo Model` when exporting.
    Please ignore the mirrored naming in models. This might be a legacy issue with Origin Furs itself - fixing it would cause rendering errors, so...

The mod additionally implements soft bones for tails/ribbons and dynamic wings. These also need to be registered in JSON files as shown below:

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

`tail_chain`: Soft bone chains attached to the torso for tails/ribbons

`tail_chain_head`: Soft bone chains attached to the head for head accessories

`wing_chain_l` & `wing_chain_r`: Bone chains for wings (left/right respectively)

Ensure all bones within a chain share consistent prefix naming in Blockbench.
