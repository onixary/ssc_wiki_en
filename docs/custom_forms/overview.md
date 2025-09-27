# Overview

## The implementation of a new data-driven custom framework is in progress, which will allow for complete customization of both the form and the animations. The information below will become outdated soon. 
## Until the new documentation is completed, please refer to the relevant examples in the GitHub repository.

This mod is not yet fully data-driven (and may remain so in the future). However, using the built-in "Empty Forms" system, you can largely create your own custom forms.

Currently, three types of "Progressive Forms" and three "Special Forms" are predefined with the following naming conventions:

Progressive Forms:


```
form_alpha_0, form_alpha_1, form_alpha_2
form_beta_0, form_beta_1, form_beta_2
form_gamma_0, form_gamma_1, form_gamma_2
```

Special Forms:


```
form_omega_sp
form_psi_sp
form_chi_sp
```

"Progressive Forms" will evolve through stages based on the Cursed Moon and Instincts mechanics, designed for players seeking the vanilla mod experience.

"Special Forms" only have one stage and are unaffected by the Cursed Moon mechanics, suitable for players who wish to play with specific forms only.

---

To obtain these empty form states through brewing:

`alpha` → `Moon Dust Potion` + `Red Dye`  
`beta` → `Moon Dust Potion` + `Yellow Dye`  
`gamma` → `Moon Dust Potion` + `Blue Dye`  

`omega` → `Moon Dust Potion` + `Green Dye`  
`psi` → `Moon Dust Potion` + `Orange Dye`  
`chi` → `Moon Dust Potion` + `Purple Dye`  

---

**Currently achievable via resource packs/data packs:**

- Customize models for any empty or existing form, including soft bone effects
- Customize abilities for any empty or existing form
- Modify form descriptions in the Book of Shape Shifter via localization files

**Currently unavailable via resource packs/data packs:**

- Adding completely new form definitions (must use pre-registered forms)
- Applying different state animations to forms
- Customizing brewing recipes for form potions
- Customizing food items (e.g., implementing "edible sticks" - similar mechanics are handled by built-in logic)

