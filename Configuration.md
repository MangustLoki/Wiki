**heightmap.core-frequency ( 0.003f )**

Modifies the noise frequency of the core height noise generator. Higher frequency for a less flat look.
***

**heightmap.river-frequency ( 0.005f )**

Modifies the noise related to river frequency. Higher frequency should mean narrower but more numerous rivers
***

**heightmap.mountain-frequency ( 0.002f )**

Modifies noise related to mountain generation. Higher frequency for narrower but more frequent mountains.
***

**heightmap.oceanic-frequency ( 0.0007f )**

Higher frequency means smaller but more frequent oceans.
***

**heightmap.land-height-amplifier ( 1f )**

Change this value to amplify the land to give it a more "Amplified" generation look.
***

**heightmap.sea-level ( 62 )**

any air at this value and below will be filled with water. This value is also used to calculate the "middlepoint" of the world's height (sea-level+13, to be precise), so all land will have a different elevation as well if you change this value. Watch out to not raise it too high or low, as Minecraft's bedrock limits are quite restrictive. Not recommended to change.
***

**heightmap.deep-sea-level ( 35 )**

Any ocean with an ocean floor at 35 or below will be considered a deep sea biome. This is important for spawning Monuments.
***

**biome.temperature-frequency ( 0.0007f )**

Changes the temperature noisemap for biomes. Larger value for smaller biomes.
***

**biome.moisture-frequency ( 0.0007f )**

Changes the moisture frequency noisemap for biomes. Larger value for smaller biomes.
***

**biome.dithering ( 0.1d )**

Between biome borders, there is a slight dithering effect where biomes "blend" into one another. A higher value for this increases the size of this blend zone, while a smaller value reduces the size.
***

**biome.clay-deposit-radius (3f)**

Decides the size of clay deposits in various biomes
***

**biome.clay-deposit-chance-out-of-thousand (3)**

Decides the chance to spawn one clay deposit in a biome. This chance is rolled 256 times per chunk.
***

**biome.min-mountain-height ( 85 )**

Any land generated at this height and above will be treated as a mountain. Subject to a random dither of 0 to 5. So this height plus 5 will be where it is 100% mountains, while at this height alone it would be a mix of mountain and flat biomes.
***

**biome.desert-mountains.place-yellow-concrete ( true )**

If this is true, desert mountains biome will use yellow concrete for a small percentage of shallow underground rock
***

**biome.desert-mountains.place-yellow-concrete-powder ( true )**

If this is true, desert mountains biome will use yellow concrete powder for their surface sand for texturing purposes.
***

**biome.river.clay.chance-out-of-thousand ( 20 )**

The chance for clay to spawn in rivers, out of 1000.
***

**biome.swamp.clay.chance-out-of-thousand ( 20 )**

The chance for clay to spawn in swamps, out of 1000.
***

**biome.lukewarm-ocean.coral.minheight ( 42 )**

The minimum Y for corals to spawn. Refers to the seabed's Y. Setting this to Y>sealevel effectively disables corals.
***

**biome.lukewarm-ocean.coral.maxheight ( 52 )**

The maximum Y for corals to spawn. Refers to the seabed's Y. Remember to make this higher than the above setting
***

**biome.dark-forest.spawn-heads (true )**

Spawn player heads in dark forests
***

**biome.badlands.plateaus.height ( 15 )**

Used for badland plateau generation. Refer to https://github.com/Hex27/TerraformGenerator/blob/master/common/src/main/java/org/terraform/biome/flat/BadlandsHandler.java
***

**biome.badlands.plateaus.sand-radius ( 7 )**

Used for badland plateau generation. Refer to https://github.com/Hex27/TerraformGenerator/blob/master/common/src/main/java/org/terraform/biome/flat/BadlandsHandler.java
***

**biome.badlands.plateaus.threshold ( 0.23 )**

Used for badland plateau generation. Refer to https://github.com/Hex27/TerraformGenerator/blob/master/common/src/main/java/org/terraform/biome/flat/BadlandsHandler.java
***

**biome.badlands.plateaus.frequency ( 0.01 )**

Used for badland plateau generation. Refer to https://github.com/Hex27/TerraformGenerator/blob/master/common/src/main/java/org/terraform/biome/flat/BadlandsHandler.java
***

**biome.badlands.plateaus.commonness ( 0.18 )**

Used for badland plateau generation. Refer to https://github.com/Hex27/TerraformGenerator/blob/master/common/src/main/java/org/terraform/biome/flat/BadlandsHandler.java
***

**biome.jungle.statue-chance-out-of-1000 (4)**

Chance to spawn a jungle statue, rolled per chunk
***

**trees.anything.enabled ( true )**

Make false to disable the specified tree.
***

**misc.custom-small-trees-from-saplings.enabled ( true )**

If this is enabled, growing trees from vanilla saplings will grow into TerraformGenerator small trees. 
***

**misc.custom-small-trees-from-saplings.big-jungle-tree ( true )**

Requires the above to be true. If this is true, spawning a big jungle tree will spawn a TerraformGenerator large jungle tree.
***

**misc.trees.only-use-logs-no-wood ( false )**

All trees will no longer generate with wood, and will instead generate with logs.
***

**misc.use-slabs-to-smooth-terrain ( true )**

Use slabs to make terrain gradients smoother. Currently done on Eroded Plains only.
***

**dev-stuff.experimental-structure-placement ( false )**

Experimental structure placement technique that may or may not be faster. You need a lighting-update plugin to use this feature, if not structures will generate without updated light values.
***

**dev-stuff.debug-mode ( false )**

Verbose printing in console. Generally, nobody should have this on but me.
***

**dev-stuff.extended-commands ( false )**

Turn to true to enable developer commands like structure placers and others. Note that these commands tend to have *no undo function*. Use with caution.
***

**dev-stuff.attempt-fixing-premature-generations ( true )**

By right, this won't do anything anymore, as newer versions of TerraformGenerator fix the underlying problem. Good to keep on in case of some kind of weird edge case.
***

**caves.allow-flooded-caves ( false )**

Turn on to allow flooded caves and ravines in oceans
***

**structures.technical.megachunk.bitshifts ( 6 )**

Size of each megachunk. By default, a bitshift of 6 means that one mega chunk is 64x64 chunks. A bitshift of, for example, 2 makes megachunks 4x4. Structures use one mega chunk to spawn, so for example, one mega chunk will only try to spawn a village house once. Making this value larger will make structures (exponentially) more sparse, while making it smaller will greatly boost structure spawn-rates. Be careful making structures too common, spigot API has a bug where world generation will never stop.
***

**structures.technical.megachunk.max-structures-per-megachunk ( 3 )**

Self explanatory. May not include some misc structures like desert wells
***

**structures.stronghold.enabled ( true )**

Enable stronghold spawning. Note that disabling this doesn't stop /locate.
***

**structures.stronghold.failsafe-y( 7 )**

If the stronghold's Y is detected to be above the ground, force strongholds to spawn at this height instead
***

**structures.stronghold.min-y ( 10 )**

Minimum Y where a stronghold will spawn. Overridden by structures.stronghold.failsafe-y if the stronghold is detected to be above the surface.
***

**structures.stronghold.max-y ( 25 )**

Maximum Y where a stronghold will spawn
***

**structures.monument.enabled ( true )**

Enable monument spawning.
***

**structures.monument.spawn-ratio ( 1.0 )**

When a location for monuments is found, this is the chance to spawn a monument. This takes in decimal values, where 0.0 is 0% and 1.0 is 100%. By default, monuments are quite rare already, so keeping this value at 1.0 is mostly acceptable.
***

**structures.pyramid.enabled ( true )**

Enable pyramidspawning.
***

**structures.pyramid.spawn-ratio ( 1.0 )**

Decrease this number if you think pyramids are too common. 1.0 is the max value.
***

**structures.pyramid.spawn-elder-guardian ( true )**

Pyramids spawn one elder guardian to prevent block breaking. 
***

**structures.farmhouse.enabled ( true )**

Enable farmhouse village houses
***

**structures.animalfarm.enabled ( true )**

Enable animal farm village houses
***

**structures.plainsvillage.enabled ( true )**

Enable villages to spawn
***

**structures.village.chunk-exclusion-zone ( 4 )**

This is the chunk radius around a village where large decorations like trees and rocks don't spawn. This gives space to the village and prevents trees from overlapping houses.
***

**structures.swamphut.enabled ( true )**

Enable spawning witch huts
***

**structures.swamphut.chance-out-of-10000 ( 10 )**

The chance for a swamp hut to spawn in each swamp chunk.
***

**structures.swamphut.spawn-mudflat-heads (true )**

Turn off to make player heads never spawn in mudflats when near witch huts.
***

**structures.desertwell.enabled ( true )**

Enable desert wells
***

**structures.desertwell.chance-out-of-10000 ( 10 )**

Chance for a desert well to spawn.
***

**structures.small-dungeon.count-per-megachunk ( 3 )**

The number of small dungeons (Drowned Dungeon and Underground Dungeons) 1 megachunk will try to spawn
***

**structures.underground-dungeon.enabled ( true )**

Enable underground mossy dungeons.
***

**structures.drowned-dungeon.enabled ( true )**

Enable in-ocean drowned dungeons. (Effectively ruins)
***

**structures.drowned-dungeon.min-chunk-y ( 52 )**

Drowned dungeons will spawn at this height and below.
***

**structures.drowned-dungeon.chance-out-of-1000 ( 200 )**

Chance to spawn a drowned dungeon
***

**structures.shipwreck.enabled ( true )**

Enable shipwreck spawning.
***

**structures.shipwreck.count-per-megachunk ( 1 )**

Max number of times to try to spawn a shipwreck in a megachunk
***

**structures.mineshaft.enabled ( true )**

Enable mineshaft spawning.
***

**structures.mineshaft.chance ( 75 )**

Chance for a mineshaft to spawn every mega chunk, out of 100. Mineshafts slow generation down significantly because of how common they are, along with their complexity to spawn, so I set this to 0 when I'm just testing stuff. Reduce this to reduce the number of mineshafts around.
***

**structures.mineshaft.min-y ( 15 )**

The minimum height where a mineshaft can spawn. Don't make this value too low, as we don't want Mineshafts to carve past bedrock.
***

**structures.mineshaft.max-y ( 30 )**

The maximum height at which a mineshaft can spawn. Don't make this value too high, if not mineshafts will begin to poke out of the ground. If mineshafts are already poking out of the ground, make this value lower, but not lower than structures.mineshaft.min-y.
***

**structures.largecave.enabled ( true )**

Enable large caves.
***

**structures.largecave.chance ( 75 )**

Chance for a large cave to spawn every mega chunk, out of 100.
***

**animals.bee.hive-frequency ( 0.02 )**

Chance for a bee hive to spawn on an oak tree, 3 d.p.
***

**animals.anything.min-herd-size ( 3 )**

Minimum number of animals to spawn per herd
***

**animals.anything.max-herd-size ( 4 )**

Maximum number of animals to spawn per herd
***

**animals.anything.chance ( 2 )**

Chance for a herd to spawn per chunk, in valid chunks (e.g. cows don't spawn in the sea, polar bears don't spawn in deserts etc), out of 100. What a valid chunk is follows vanilla spawning behaviour.
***

**ore.anything.chance-per-chunk ( 70 )**

This chance refers to the chance of this ore spawning per try to spawn 1 vein.
***

**ore.anything.max-vein-size ( 30 )**

Maximum size of one vein
***

**ore.anything.max-vein-count ( 50 )**

Maximum number of times to try to spawn this ore in a chunk
***

**ore.anything.common-spawn-height ( 128 )**

Height at which ore spawns are common. Related to the setting below
***

**ore.anything.max-spawn-height ( 131 )**

This ore can spawn up to this height, but it is rarer if it's above common-spawn-height
***

**ore.anything.min-spawn-height ( 5 )**

Refers to the minimum Y at which this ore can spawn
***