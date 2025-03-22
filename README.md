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
### [server.properties](https://minecraft.wiki/w/Server.properties)
sync-chunk-writes ```false```

network-compression-threshold** ```256```
