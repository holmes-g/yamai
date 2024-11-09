## How to use

The best way is to install the mod [Schematic Browser Reworked](https://github.com/StormyBytes/mindustry-schematic-browser), which lets you insert schematics from GitHub repositories. Schematic Browser can be installed in Mindustry using the built-in mod browser. In the “Schematic Repositories” view, click on “Add Repo” and type “holmes-g/yamai”, confirm with “Add Repo”, then click on “Fetch” to update schematics from configured repositories.

## Features

Functions:

* Mine copper, lead, sand, coal, titanium, scrap, and beryllium using pulsar, quasar, mono, poly, and mega. Scrap and poly are disabled by default.
* Remove flags from units that are no longer controlled. This includes all Serpulo and Erekir units controllable by logic.
* Repair miner units when they are damaged. They will move to the closest repair point, so long as it has power.
* Repair damaged allied buildings with poly and mega, when in range.
* Shoot at enemy units with poly and mega, when in range.
* Flee from active enemy turrets and spawn points.


The design attempts to avoid compromising mining speed when controlling many units and this has some tradeoffs with other features.

Other features:

* Scalability: if multiple copies of the AI are built, this will not cause disruption and will increase speed so long as all copies have the same ores enabled with the same priorities.
* Dynamic allocation of processors to unit types: if a unit type is not in use because it is disabled, the team has no units of that type, or core is sufficiently full of all items that it can mine, mining processors for that unit type are allocated to other unit types. This avoids processors remaining idle that can be used to accelerate mining instead.

## Configuration

Configuration is done by editing variables at the top of the manager processor, normally a micro processor close to the message block.

* Ores: `copperPriority`, `leadPriority`, `sandPriority`, `coalPriority`, `titaniumPriority`, `scrapPriority`, and `berylliumPriority` can be set to 0 to disable that ore, 1 to enable it, or to a number less than or greater than 1 to give it lower or higher priority relative to other ores.
* Units: `monoEnabled`, `polyEnabled`, `megaEnabled`, `pulsarEnabled`, and `quasarEnabled` can be set to 1 to enable that unit or 0 to disable it.
* `coreFullThreshold` is a number between 0 and 1. When all items that can be mined by a unit and are enabled and available on the map have reached that proportion of core capacity, the unit is released.

Disabling all units or all ores will disable mining fully.

## Frequently asked questions

### Which features are included in each variant?

| Variant | Mining | Deflagger | Self-repair | Building repair | Enemy attack | Avoiding danger |
| --- | --- | --- | --- | --- | --- | ---
| 6 micro processors | ✔️ | :x: | :x: | :x: | :x: | :x:
| 5 logic processors | ✔️ | ✔️ | :x: | :x: | :x: | :x:
| 7 logic processors | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ | :x:
| 8 logic processors | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ | :x:
| 14 logic processors | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ | ✔️
| 6 hyper processors | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ | :x:
| 7 hyper processors | ✔️ | ✔️ | ✔️ | ✔️ | ✔️ | :x:

All variants support all ores and unit types. The cheapest variants do not include support functions. Other variants offer similar features, but with different processor speeds and overdrive or input types.

The switch variant has switches for enabling or disabling poly, mega, pulsar, and quasar.

### How to get non-buildable items inside Erekir cores?

Erekir cores incinerate the non-buildable items from Serpulo (sand, coal, spore pods, blast compound, and pyratite) instead of adding them to the core. However, Serpulo containers and vaults attached to Erekir cores do not incinerate these items when they are deposited by units. All variants of YAMAI except the micro-processor variant attempt to deposit in core-attached storage, so, if you have containers or vaults attached to Erekir cores, miner units will use them to avoid incinerating the items.
