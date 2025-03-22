# Minecraft server optimization guide
## Before you read this...
Yes, this is a copy of [YouHaveTrouble's guide](https://github.com/YouHaveTrouble/minecraft-optimization). I did not make this guide myself. This repository summarizes and reorders the aforementioned guide for all of you people who have no patience to read such long texts.

This guide applies for version 1.21+. Some things may still apply to 1.15 - 1.20.
## Server software
Consider using [Paper](https://papermc.io/) for performance or [Purpur](https://purpurmc.org/) for extra customizations.

[Leaf](https://www.leafmc.one/) has better performance since it is a fork of Paper, Purpur and many other softwares. However, it is still in development. Use at your own risk.
## Map pre-generation
*Unless you run your server on terrible, single-threaded, or limited processors, this is usually not necessary.*

Use [Chunky](https://github.com/pop4959/Chunky) to pre-generate your world's chunks. This may take hours or days depending on your server's performance.
## Configurations
All of the following values are recommended starting values pulled from [YouHaveTrouble's guide](https://github.com/YouHaveTrouble/minecraft-optimization).

For config options with multiple lines of values, remember to **check the indentation**. Your server probably won't start with 1 extra or missing space in any config file.
### [server.properties](https://minecraft.wiki/w/Server.properties)
sync-chunk-writes - `false`

network-compression-threshold - `256`

simulation-distance - `4`

view-distance - `7`

### [bukkit.yml](https://docs.papermc.io/paper/reference/bukkit-configuration)
spawn-limits

```
    monsters: 20
    animals: 5
    water-animals: 2
    water-ambient: 2
    water-underground-creature: 3
    axolotls: 3
    ambient: 1
```

ticks-per

```
    monster-spawns: 10
    animal-spawns: 400
    water-spawns: 400
    water-ambient-spawns: 400
    water-underground-creature-spawns: 400
    axolotl-spawns: 400
    ambient-spawns: 400
```

### [spigot.yml](https://docs.papermc.io/paper/reference/spigot-configuration)
view-distance - `default`

mob-spawn-range - `3`

entity-activation-range

```
      animals: 16
      monsters: 24
      raiders: 48
      misc: 8
      water: 8
      villagers: 16
      flying-monsters: 48
```

entity-tracking-range

```
      players: 48
      animals: 48
      monsters: 48
      misc: 32
      other: 64
```

tick-inactive-villagers - `false`

nerf-spawner-mobs - `true`

merge-radius

```
      item: 3.5
      exp: 4.0
```

hopper-transfer - `8`

hopper-check - `8`
### [config/paper-world-defaults.yml](https://docs.papermc.io/paper/reference/world-configuration)
delay-chunk-unloads-by - `10s`

max-auto-save-chunks-per-tick - `8`

prevent-moving-into-unloaded-chunks - `true`

entity-per-chunk-save-limit

```
    area_effect_cloud: 8
    arrow: 16
    breeze_wind_charge: 8
    dragon_fireball: 3
    egg: 8
    ender_pearl: 8
    experience_bottle: 3
    experience_orb: 16
    eye_of_ender: 8
    fireball: 8
    firework_rocket: 8
    llama_spit: 3
    potion: 8
    shulker_bullet: 8
    small_fireball: 8
    snowball: 8
    spectral_arrow: 16
    trident: 16
    wind_charge: 8
    wither_skull: 4
```

despawn-ranges *(warning: applying these values may break mob farms, leave default as in the config file if possible.)*

```
      ambient:
        hard: 72
        soft: 30
      axolotls:
        hard: 72
        soft: 30
      creature:
        hard: 72
        soft: 30
      misc:
        hard: 72
        soft: 30
      monster:
        hard: 72
        soft: 30
      underground_water_creature:
        hard: 72
        soft: 30
      water_ambient:
        hard: 72
        soft: 30
      water_creature:
        hard: 72
        soft: 30
```

per-player-mob-spawns - `true`

max-entity-collisions - `2`

update-pathfinding-on-block-update - `false`

fix-climbing-bypassing-cramming-rule - `true`

armor-stands -> tick - `false`

armor-stands -> do-collision-entity-lookups - `false`

tick-rates

```
  behavior:
    villager:
      validatenearbypoi: 60
      acquirepoi: 120
  sensor:
    villager:
      secondarypoisensor: 80
      nearestbedsensor: 80
      villagerbabiessensor: 40
      playersensor: 40
      nearestlivingentitysensor: 40
```

alt-item-despawn-rate

```
      enabled: true
      items:
        cobblestone: 300
        netherrack: 300
        sand: 300
        red_sand: 300
        gravel: 300
        dirt: 300
        short_grass: 300
        pumpkin: 300
        melon_slice: 300
        kelp: 300
        bamboo: 300
        sugar_cane: 300
        twisting_vines: 300
        weeping_vines: 300
        oak_leaves: 300
        spruce_leaves: 300
        birch_leaves: 300
        jungle_leaves: 300
        acacia_leaves: 300
        dark_oak_leaves: 300
        mangrove_leaves: 300
        cherry_leaves: 300
        cactus: 300
        diorite: 300
        granite: 300
        andesite: 300
        scaffolding: 600
```

redstone-implementation - `ALTERNATE_CURRENT`

hopper -> disable-move-event - `false`

hopper -> ignore-occluding-blocks - `true`

tick-rates -> mob-spawner - `2`

optimize-explosions - `true`

treasure-maps -> enabled - `false`

treasure-maps -> find-already-discovered

```
      loot-tables: true
      villager-trade: true
```

tick-rates -> grass-spread - `4`

tick-rates -> container-update - `1`

non-player-arrow-despawn-rate - `20`

creative-arrow-despawn-rate - `20`
## Troubleshooting lag
Paper offers the `/mspt` command, which shows you how long it takes for your server to tick once. If the first and second number in the command's output are below 50, your server is completely fine!

You may install [Spark](https://spark.lucko.me/), which is a great performance monitoring plugin. It also helps other (and you) find out what is causing lag (plugins, data packs...).
## Miscellaneous
Check out [Aikar's Flags](https://docs.papermc.io/paper/aikars-flags) for optimized startup flags.

If you're using Paper or its forks (which you should), consider configuring its [built-in Anti-Xray](https://docs.papermc.io/paper/anti-xray).
## Plugins to avoid
Don't install plugins that claim to *improve performance* (either by clearing RAM, removing items, stacking mobs...) as they may cause more lag rather than making your server smoother.

Anti-Xray plugins may lag your server since they are very resource-dependent. Use [Paper's built-in Anti-Xray](https://docs.papermc.io/paper/anti-xray) instead, it is good enough to prevent common forms of Xray-ing (resource packs...).
