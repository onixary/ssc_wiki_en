# Form Definition JSON Configuration

The form definition JSON file is used to configure animations, form types, body types, and other properties of custom forms

It needs to be placed in the `/data/example_namespace/ssc_form` directory, with the same name as your custom form ID

### Form Definition JSON Format

```json
{
  "__comment__": "See PlayerFormBase for details",
  "groupID": "example_namespace:example_group",
  "__groupID_comment__": "Group ID used for registering groups, corresponding to the datapack structure",
  "groupIndex": 5,
  "__groupIndex_comment__": "Index within group used for transformation logic",
  "phase": "PHASE_SP",
  "__Phase_comment__": "Transformation phase usually matches groupIndex. Enum:[PHASE_CLEAR, PHASE_0, PHASE_1, PHASE_2, PHASE_3, PHASE_SP]",
  "bodyType": "FERAL",
  "__BodyType_comment__": "Body type. Enum:[NORMAL, FERAL]",
  "isCustomForm": true,
  "originID": "example_namespace:form_example",
  "__originID_comment__": "OriginID works with the built-in Origin mod, corresponding to the origin layer name. **Must be registered in data/[NameSpace]/origins**",
  "originLayerID": "origins:origin",
  "__originLayerID_comment__": "OriginLayerID works with OriginFur **Highly not recommended to modify**",
  "hasSlowFall": false,
  "overrideHandAnim": false,
  "canSneakRush": false,
  "canRushJump": false,
  "anim": [
    {
      "state": "ANIM_IDLE",
      "animID": "example_namespace:form_example_idle"
    },
    {
      "state": "ANIM_SNEAK_IDLE",
      "animID": "shape-shifter-curse:form_feral_common_sneak_idle"
    }
  ],
  "__anim_comment__": "Animation list. State is defined in PlayerAnimState",
  "animDefault": {
    "animID": "shape-shifter-curse:form_feral_common_idle",
    "speed": 1.0,
    "fade": 2
  },
  "__animDefault_comment__": "Default animation. If not present, this key can be omitted"
}
```

The comment fields in the example should have explained the meaning of the corresponding fields. Below are additional explanations for some fields:

### groupID

Used to identify which group the current form belongs to

Only forms under the same `groupID` with correctly registered `groupIndex` and `phase` can trigger the transformation logic normally of progressive forms.
For example, `bat_0`, `bat_1`, `bat_2`, `bat_3` should all be in the `example_namespace:bat` group

### groupIndex and phase

Identify the index within the group and transformation phase respectively, used for the transformation logic of progressive forms

They correspond one-to-one, with meanings and relationships as follows. Please refer to the table below to register the corresponding groupIndex and phase according to the stage of your desired custom form:

| groupIndex: |        -2         |        -1        |                       0                        |      1      |      2      |         3         |     5      |
|:-----------:|:-----------------:|:----------------:|:----------------------------------------------:|:-----------:|:-----------:|:-----------------:|:----------:|
|   phase:    |    PHASE_CLEAR    |   PHASE_CLEAR    |                    PHASE_0                     |   PHASE_1   |   PHASE_2   |      PHASE_3      |  PHASE_SP  |
|    Form Stage:    | Form when mod content is not enabled, useless for custom | Placeholder for original form before transformation, useless for custom |        First stage of progressive forms        | Second stage of progressive forms | Third stage of progressive forms | Fourth stage of progressive forms, i.e., permanent stage | Special form that can be restored at any time |

For example: `groupIndex` of `bat_0` should be set to `0`, and `phase` should be set to `PHASE_0`

groupIndex 4 is currently unused, reserved for future special forms

### bodyType

Humanoid is `NORMAL`, quadrupedal form is `FERAL`

This field only affects camera height and item rendering methods. Under `FERAL` bodyType, you need a complete set of animations to achieve the desired effect. It is recommended to reuse existing animations in the project to save effort

### isCustomForm

Set to `true`. This field affects the command for changing forms. When `true`, it will appear in `set_custom_form` instead of `set_form`

### originID

This field needs to match the name in origin_layer

A form needs to correspond to an origin, used to implement form abilities and link with the form model

### anim

Used to register animations for different states, where the `state` field corresponds to states in PlayerAnimState, and the `animID` field corresponds to your namespace name and exported animation JSON file name

The currently implemented state enum can be found in [PlayerAnimState](https://github.com/onixary/shape-shifter-curse-fabric/blob/master/src/main/java/net/onixary/shapeShifterCurseFabric/player_animation/PlayerAnimState.java). The values and meanings are listed below:

| state |         Meaning         |
|:-----:|:-----------------------:|
| ANIM_IDLE |        Standing still        |
| ANIM_SNEAK_IDLE |        Sneaking idle        |
| ANIM_WALK |         Moving         |
| ANIM_RUN |         Sprinting         |
| ANIM_JUMP |         Jumping         |
| ANIM_FALL |         Falling         |
| ANIM_CLIMB_IDLE |        Climbing idle        |
| ANIM_CLIMB |        Climbing movement        |
| ANIM_SWIM |        Swimming state        |
| ANIM_SWIM_IDLE |        Idle in water        |
| ANIM_BOAT_IDLE |        Boat idle        |
| ANIM_RIDE_IDLE |        Riding idle        |
| ANIM_ELYTRA_FLY |        Elytra flying        |
| ANIM_CREATIVE_FLY |       Creative flight       |
| ANIM_CRAWL |        Crawling movement        |
| ANIM_CRAWL_IDLE |        Crawling idle        |
| ANIM_SLOW_FALL |         Slow falling         |
| ANIM_ATTACK_ONCE |    Attack once (click left button once)    |
| ANIM_TOOL_SWING |   Swing tool (hold left button for mining, etc.)    |
| ANIM_SNEAK_RUSH |   Sneak rush (used for ocelot form in vanilla)   |
| ANIM_RUSH_JUMP | Rush jump (used for ocelot and axolotl forms in vanilla) |
| ANIM_SLEEP |         Sleeping         |
| ANIM_SNEAK_JUMP |      Jump while holding sneak       |
| ANIM_SNEAK_FALL |      Falling while holding sneak       |
| ANIM_SNEAK_ATTACK_ONCE |    Attack once while holding sneak (click left button once)|
| ANIM_SNEAK_TOOL_SWING | Swing tool while holding sneak (hold left button for mining, etc.) |

### animDefault

Default animation. When no other animations are available, this animation will be played. Usually registered as the animation for the `ANIM_IDLE` state

For `FERAL` bodyType, if this field is not registered, an upright posture will appear when stationary