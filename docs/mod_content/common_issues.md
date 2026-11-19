### FAQ:

**The game fails to launch after updating to 1.10.0 because of missing GeckoLib?**

In version 1.10.0, the rendering dependency migrated from `AzureLib` to **`GeckoLib` (4.x required; incompatible with 5.x)**, and `Satin API` is no longer required.

Please install `GeckoLib 4.x` and `Pehkui` (alongside Fabric API). `AzureLib` and `Satin API` can be removed.

**How do I trigger active form abilities (such as Water Explosion or Perk skills)?**

Version 1.10.0 adds `Active Power (1)` through `Active Power (6)` keybinds, which are **unbound by default**. Go to `Controls → Key Binds`, find the Shape Shifter Curse category, and assign your preferred keys.

**Why doesn't Milk cure Transformation Status Effects anymore?**

Starting from version 1.10.0, `Milk` no longer cures `Transformation Status Effects`. Use a `Golden Apple` (regular or enchanted) or an `Inhibitor` instead.

**Why can't I craft form trinkets in a Crafting Table anymore?**

Starting from version 1.10.0, the 13 base form trinkets moved to the `Shape Shifter Altar`. See the `Shape Shifter Altar & Catalyst Cores` section for details.

**My character skin was replaced?**

After enabling mod content, your skin is replaced with the mod's built-in skin (a.k.a. *the shifter*) for visual consistency with form models and out of respect for custom characters.

You can restore your own skin using `/shape_shifter_curse keep_original_skin true`.

**Does this work on multiplayer servers?**

Yes! Server compatibility has been supported since version 1.0.5. If you encounter any issues, please open an issue on GitHub.

**I don't like the First-person Model mod's perspective**

Since version 1.0.62, form arms render properly in vanilla first-person view (though First-person Model is still recommended for stronger immersion).

**Can I create my own custom forms?**

Yes! You can create custom forms using a datapack + resource pack, including custom models, abilities, instinct mechanics, form potions, and codex text.

Please refer to the `Creating Custom Forms` section of this wiki and the example pack in the repository (note: version 1.10.0 updated the custom form and model config formats; older packs must migrate accordingly).

**How do I transform into other forms?**

You can follow the in-game advancements and recipes for guidance, or check the wiki pages if you get stuck.

**Are some forms permanent?**

Yes, permanent forms were introduced in version 1.0.4. Reaching Permanent Phase unlocks each form's Perk Tree, and certain forms can also switch into Sub-Forms.

**I accidentally lost my Book of Shape Shifter**

You can craft a new one using `Untreated Moondust` + `Book`.

**Is this mod SFW?**

Of course!
