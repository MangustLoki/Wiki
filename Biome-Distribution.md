In newer versions, a set of config options exist that allow you to tune biome distribution and climates.

```
climate:
  humid-vegetation:
    minimum-moisture: 0.0
    maximum-moisture: 4.0
    minimum-temperature: -0.35
    maximum-temperature: 4.0
  snowy:
    minimum-moisture: -4.0
    maximum-temperature: -2.7
    minimum-temperature: -4.0
    maximum-moisture: 4.0
  hot-barren:
    maximum-temperature: 4.0
    minimum-moisture: -4.0
    maximum-moisture: -1.0
    minimum-temperature: 1.0
  dry-vegetation:
    minimum-moisture: -4.0
    maximum-moisture: 0.0
    maximum-temperature: 4.0
    minimum-temperature: -0.35
  cold:
    maximum-temperature: -0.5
    minimum-moisture: -4.0
    maximum-moisture: 4.0
    minimum-temperature: -4.0
```

They represent a graph that looks like this
![](https://imgur.com/ctDR363.png)
_Biomes may not be up to date, this just shows the general idea of things_

Transition has the lowest priority, so while its moisture and temperature span the entire graph, it will be covered by other climates.

The corner climates have highest priority and will always override the others (snowy, hot barren, humid vegetation)

As such, if you want to shrink the Dry Vegetation climate, you can raise minimum-temperature for dry vegetation by a little and see if it works.

An easy way to visualize the changes without flying around the world is to run the */terra biomedistrib* command from console. This command requires that you enable extended commands in config, but it will help you see how common all the biomes are.