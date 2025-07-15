# Update Log

### 1.0.0 - 1.0.2  
Initial version release and subsequent bug fixes.

### 1.0.31 - 1.0.32  
image  
Introduced the first quadrupedal form: feral_cat_sp.  
Resolved various issues related to quadrupedal forms, implementing a complete set of animations with corresponding first-person and third-person item perspectives.  
Added placeholder quadrupedal form phi_sp for customization purposes.  
Relevant bug fixes implemented.

### 1.0.4 - 1.0.41  
image  
Added new familiar_fox form.  
Implemented permanent form mechanics along with two new permanent forms: familiar_fox_3 and ocelot_3.  
Relevant bug fixes applied.

### 1.0.5  
**Server Compatibility Achieved**  
Special thanks to GitHub user [solunareclipse1](https://github.com/solunareclipse1) for providing key insights. After development efforts, the mod should now function correctly on servers.  

Note: Testing has only occurred in development environments, not actual server deployments. We recommend against installing this on primary servers until further verification.

**Important: Manual Save Migration Required**  
To accommodate server compatibility, this version moves save files from previous non-standard locations to development-conventional paths. To preserve your mod progress, manual migration is required:  

1. Locate old save location:  
`(MINECRAFT_VERSION)/Config/shape_shifter_curse_fabric/(WORLD_NAME)`  
You'll find multiple files beginning with your UUID. Copy these files.  
Cursed Moon event data requires no migration.  

2. Transfer to new save location:  
`(MINECRAFT_VERSION)/saves/(WORLD_NAME)/data/shape-shifter-curse`  
If the shape-shifter-curse folder doesn't exist, create it and paste your copied files.  
Migration is now complete.  

**Bug Fixes**  
- Resolved mob aggression issues with familiar_fox form  
- Fixed occasional display of player arm models in feral forms  

**Form Mechanism Improvements**  
- Axolotl mechanics optimized based on player feedback for improved engagement  
- Adjusted instinct triggers for several forms to create more natural progression
