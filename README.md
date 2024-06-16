## How to use

The best way is to install the mod [Schematic Browser Reworked](https://github.com/StormyBytes/mindustry-schematic-browser), which lets you insert schematics from GitHub repositories. Schematic Browser can be installed in Mindustry using the built-in mod browser. In the “Schematic Repositories” view, click on “Add Repo” and type “holmes-g/yamai”, confirm with “Add Repo”, then click on “Fetch” to update schematics from configured repositories.

## Features

Functions:

* Mine copper, lead, sand, coal, titanium, scrap, and beryllium using pulsar, quasar, mono, poly, and mega. Scrap and poly are disabled by default.
* Remove flags from units that are no longer controlled. This includes all Serpulo and Erekir units controllable by logic.
* Repair miner units when they are damaged. They will move to the closest repair point, so long as it has power.
* Repair damaged allied buildings with poly and mega, when in range.
* Shoot at enemy units with poly and mega, when in range.

The design attempts to avoid compromising mining speed when controlling many units and this has some tradeoffs with other features.

Other features:

* Scalability: if multiple copies of the AI are built, this will not cause disruption and will increase speed so long as all copies have the same ores enabled.
* Dynamic allocation of processors to unit types: if a unit type is not in use because it is disabled, the team has no units of that type, or core is sufficiently full of all items that it can mine, mining processors for that unit type are allocated to other unit types. This avoids processors remaining idle that can be used to accelerate mining instead.

## Frequently asked questions

### How to configure which ores and units are enabled?

Ores and units to enable are configured by editing variables at the top of the manager processor, normally a micro processor close to the message block. There are 12 variables, `copperEnabled`, `leadEnabled`, `sandEnabled`, `coalEnabled`, `titaniumEnabled`, `scrapEnabled`, `berylliumEnabled`, `monoEnabled`, `polyEnabled`, `megaEnabled`, `pulsarEnabled`, and `quasarEnabled`, each of which can be set to `true` (equivalently `1`) to enable or to `false` (equivalently `0`) to disable.

Disabling all units or all ores will disable mining fully.

### Which features are included in each variant?

All variants support all ores and unit types. The variant with micro processors does not include a deflagger or support functions and the variant with five logic processors includes a deflagger but does not include support functions. All other variants support all functions, but with different processor speeds and overdrive or input types.

### How to get non-buildable items inside Erekir cores?

Erekir cores incinerate the non-buildable items from Serpulo (sand, coal, spore pods, blast compound, and pyratite) instead of adding them to the core. However, Serpulo containers and vaults attached to Erekir cores do not incinerate these items when they are deposited by units. All variants of YAMAI that include the support functions attempt to deposit in core-attached storage, so, if you have containers or vaults attached to Erekir cores, miner units will use them to avoid incinerating the items.

Some of the sand and coal will still be incinerated because the mining processors are faster than the support processors and they deposit into core to avoid reducing mining speed. If you need sand or coal in Erekir cores and you know that all your cores have storage attached to them, you can manually edit the mining processors to change the amount deposited to core to 0. This ensures that none of the sand or coal gets incinerated, but it will cause issues if some cores do not have containers or vaults attached.
