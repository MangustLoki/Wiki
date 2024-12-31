## What happened to the "alpha" tag? Did anything significant change with the plugin?

No significant change occurred for the removal of the alpha tag. TerraformGenerator was marked as an alpha project. That didn't mean that there were major bugs present all the time, it just used to mean that the plugin was currently under active development for core features. However, core features (not counting new structures etc) have remained the same for a very long time and the alpha tag had lost its meaning. 

Server owners are still expected to test their generation thoroughly to check it against their server's needs regardless of whether or not the plugin is in alpha. TerraformGenerator takes a while to pregenerate as it processes chunks more slowly than vanilla. This makes mistakes identified later on annoying to fix.

## What is the difference between [TerraformGenerator](https://www.spigotmc.org/resources/terraformgenerator-1-16-5-1-20-1.75132/) and [TerraformGenerator Premium](https://www.spigotmc.org/resources/terraformgenerator-premium.98309/)?

Nothing.

TerraformGenerator will always be free and open source. I added a premium version because the free one was giving about $20 a year in donations. The two versions are exactly the same and buying TerraformGenerator Premium is just a means to support development. 

## What RAM/CPU do I need to run this plugin?

I test the plugin on bare metal, with 3GB ram and an Intel i7 (i7-10510U CPU @ 1.80GHz 2.30 GHz). However, this isn't listed on the spigot page because the plugin is not specially optimised to work on low specs. Additionally, many servers tend to be cloud-hosted, and sometimes server hosts share resources, so their stated resources are not always what you're using. This is especially bad for this plugin as its world generation can be much slower than vanilla's. Solve server load issues regarding world generation by pregenerating.

## Plugin not working

**Q:** I installed TerraformGenerator, why is my server crashing/why is my world still vanilla?
   
**A:** If you've followed the Getting Started tutorials ([[1|Getting Started#method-one]] or [[2|Getting Started#method-two]]) and it still isn't working, you should find the startup log of TerraformGenerator, and the reason why it's disabled/not working should be there. You can always join our [discord server](https://discord.gg/yW7JcqM) for further support

***

**Q:** Can I use TerraformGenerator with an existing world? Can I update TerraformGenerator/edit config without deleting my world?

**A:** No, you absolutely cannot. If you deploy TerraformGenerator on an existing world (be it generated with an older version, or by vanilla, or by another generator), new chunks generated in that world risk being out of place. You will see stuff like this:

![](https://imgur.com/wxNIcqE.png)

Note that TerraformGenerator cannot undo generated chunks. This is a mistake that cannot be undone without a backup. 

Don't do it.

***

## Pre-generating the World

**Q:** What is pre-generation and when should I do it?

**A:** When using terraformgenerator, it is heavily recommended to *always* pre-generate. The plugin was not designed with live generation in mind. 

Pre-generation is pre-emptively generating your world's chunks up to a certain world border that you set, so players don't trigger chunk generation when they play. This is so the plugin will never cause lag in your server's live environment where players are trying to play the game. 

***

**Q:** How do I pre-generate the world?
   
**A:** There are a _lot_ of plugins that can do this, I'll list some of them:

* [Fast Chunk Pregenerator](https://www.spigotmc.org/resources/fast-chunk-pregenerator.74429/) - `/fcp start <radius> [worldName]`
* [Chunkmaster](https://www.spigotmc.org/resources/chunkmaster.71351/) - `/chm generate [worldName] <radius> `
* [Chunky](https://www.spigotmc.org/resources/chunky.81534/) - `/chunky shape <shape>`, `/chunky center <x> <z>`, `/chunky radius <radius>` and lastly, `/chunky start`

The commands listed _can_ be used. However, we recommend taking a look at their respective wiki/spigot page for more information. Pre-generating the world may take some time and a bit of resources. Don't pre-generate while players are online.

***

## Errors

**Q:** I got an error in the console. What should I do?
   
**A:** Depends on the error.

### Red Paper Watchdog Stack Trace

```
[14:03:15] [Paper Watchdog Thread/ERROR]: --- DO NOT REPORT THIS TO PAPER - THIS IS NOT A BUG OR A CRASH - git-Paper-344 (MC: 1.16.4) ---
[14:03:15] [Paper Watchdog Thread/ERROR]: The server has not responded for 10 seconds! Creating thread dump
[14:03:15] [Paper Watchdog Thread/ERROR]: ------------------------------
[14:03:15] [Paper Watchdog Thread/ERROR]: Server thread dump (Look for plugins here before reporting to Paper!):
```

If you get this message during pre-generation, you can apply the fix below if it's too spammy.

If you didn't pre-generate, and you're getting this error, go pre-generate. **If you did not pre-generate, do not apply the fix below, it will not fix your lag. Pregeneration is the only way to fix lag caused by TerraformGenerator.**

You can suppress this stack trace by making the following changes in paper-global.yml in the config folder (or paper.yml if you’re on a version older than 1.19):
```
  watchdog:
    early-warning-every: 5000000
    early-warning-delay: 10000000
```
This will effectively disable watchdog. After you're done with all the world generation, turn those settings back to their originals. 

The watchdog is meant to detect sources of lag and to stop the server if it detects a long freeze. World generation is already known to be a laggy process, so we don't want watchdog warning us that world generation is laggy. So while pre-generating, it may be a good idea to suppress watchdog, especially if your machine has very little memory or a slow cpu.

### Text Encoding Startup Failure

**As for version 16.1.1, a fix was implemented by a contributor that patches this problem entirely. If you still see this problem in 16.1.1 or newer, please report it in issues or in the discord.**

Some Java VMs have a non-utf8 text encoding, which may cause some problems with loading. An error will look like so (notice the non-ascii i):
```
net.minecraft.ResourceKeyInvalidException: Non [a-z0-9/._-] character in path of location: terraformgenerator:crystallıne_cluster
```

The solution is to add these flags to your JVM:
```
-Dfile.encoding=UTF-8 -Duser.language=en
```

### /reload

Don't use /reload. Terraformgenerator (along with many other complex plugins) will break when you do so.

### Server crashes

If the errors result in players being kicked out because the server is shutting down, or you get an internal error of some sort, you have probably encountered a bug. You can get support and report bugs in discord. 

If it looks like paper's watchdog terminated the server **and** you happened to be pre-generating, you can apply the fix above in server freezes.

### Others

If an error is thrown, and it isn't due to paper's watchdog, report it in the [discord server](https://discord.gg/yW7JcqM) for the fastest response.

**A note on CraftBukkit**  
Using TerraformGenerator on a Server running CraftBukkit may not work and could crash the server.  
We recommend you use [Paper](https://papermc.io) as it improves performance compared to CraftBukkit and Spigot.

## Requests

### Feature Requests

**Q:** I want to make a feature request

**A:** Use the discord server for it. If one of the devs like the idea, it may be added. Note that there's no guarantee that any requests will be definitively accepted.

***

**Q:** What determines the priority of a feature request?

**A:** Features that are present in vanilla will generally get a higher priority, along with features that are hardwired into vanilla gameplay.

Apart from that, it depends on developer discretion.

***

**Q:** Is there an ETA for X feature?

**A:** TerraformGenerator isn't a full time project by any means, and all the developers working on it are doing it in their own (possibly volatile) free time. As a result, there will not be an official ETA for anything, and any ETAs given are not guarantees or promises.

## Configuration

***

**Q:** How can I increase Biome size?

**A:** Increase biome.biomesection-bitshifts in config. By default (with a value of 7), one biome section is 128 (2 pow 7) blocks wide. You cannot increase this number by too much, the plugin tries to optimise generation based on section size. That means that there exists an upper bound based on how much memory the server has. I recommend that you only change this value by 1 or 2.

***

**Q:** How do I disable biome X

**A:** There is a "weight" option for each biome in the config. This number represents a biome's relative frequency within its climate. For example, the hot barren climate has 2 flat biomes: deserts and badlands. A weight of 6 for deserts and a weight of 1 for badlands means that 1/7 of all flat biomes in hot barren climates will be badlands (and the rest deserts)

Setting badlands' weight to 0 will "disable" badlands.

Do not set all the biome weights within a single climate to 0, it won't work. 

***

**Q:** I want to make 0,0 flat so I can build spawn

**A:** Set heightmap.spawn-flat-radius to your radius in blocks. This radius from 0,0 will be a uniform-ish level and rivers and trees will not spawn in this radius. It does not have a fantastic blend with the surroundings on the edges of the radius and may need manual fixing from builders.

***

**Q:** I want to make the whole world one biome

**A:** The plugin does not support a lot of customisation, so it isn't possible to make the world one biome. It is minimally one of every type of biome. For example, take this config:

```yaml
 single:
    highmountain: BADLANDS_CANYON_PEAK
    land: DESERT
    ocean: DRY_OCEAN
    mountain: BADLANDS_CANYON
    deepocean: DEEP_DRY_OCEAN
```

This will make all flat biomes deserts, all oceans dry oceans and all mountains badlands canyons. You can't have a world where there are only mountains, or only deserts etc. This is as close as you can get to a world that is only desert. You can find a list of biomes in the source code [here](https://github.com/Hex27/TerraformGenerator/blob/master/common/src/main/java/org/terraform/biome/BiomeBank.java).

***

**Q:** How can I make all structures more frequent?

**A:** Decrease structures.technical.megachunk.numbiomesections. The default is 4 biome sections wide (1 structure every 512x512 blocks)

***

**Q:** Can I remove the plugin after I've pregenerated the world?

**A:** Structure locating (including eye of enders and cartographers) will break, and biomes that use custom colours will revert back to vanilla colours. If that's fine, you can remove the plugin. Monuments and Pillager watchtowers will continue to spawn their respective monsters even without the plugin.

***

**Q:** Does TerraformGenerator add custom biomes? What are their in-game tags?

**A:** Yes it does. Most biomes will re-use vanilla biomes (though not literally all the biomes, so that achievement where you visit every biome doesn't actually work with the plugin). However, there are some custom biome colour biomes that the plugin will add. You can find a list in the code [here](https://github.com/Hex27/TerraformGenerator/blob/master/common/src/main/java/org/terraform/biome/custombiomes/CustomBiomeType.java).

For example, a tag would look like `terraformgenerator:muddy_bog`