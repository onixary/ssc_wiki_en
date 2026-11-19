# Available Mod Commands

### Administrator Commands

- Trigger form transformation: `/shape_shifter_curse transform_to_form <USER> <FORM>`

- Trigger datapack custom form transformation: `/shape_shifter_curse transform_to_dynamic_form <USER> <FORM>`

- Trigger sub-form transformation: `/shape_shifter_curse transform_to_sub_form <USER> <FORM>`

- Set form directly: `/shape_shifter_curse set_form <USER> <FORM>`

- Set datapack custom form directly: `/shape_shifter_curse set_dynamic_form <USER> <FORM>`

- Set sub-form directly: `/shape_shifter_curse set_sub_form <USER> <FORM>`

- Manage current form Perk Tree: `/shape_shifter_curse perk <list | toggle_free <BOOLEAN> | unlock_all | reset_all>`

- Trigger the Cursed Moon event immediately: `/shape_shifter_curse jump_to_next_cursed_moon`

- Adjust world time: `/shape_shifter_curse world_time <set | add> <TIME>`

### All User Commands

- Toggle keeping your original player skin: `/shape_shifter_curse keep_original_skin <BOOLEAN>`

- Open or manage form color presets: `/shape_shifter_curse form_color <menu | list | save | load | delete>`

- Set form color via command: `/shape_shifter_curse set_form_color ...`

### Game Rules

- Control whether new players start with the server-configured initial form (default `true`; requires `enableInitialForm = true` in common config): `/gamerule sscUseInitialForm <true | false>`
