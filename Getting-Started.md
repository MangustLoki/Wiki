[TerraformGenerator]: https://www.spigotmc.org/resources/75132/

# Installation

## Prerequisites

Ensure that you have at least Java 16.

## Step one: Install TerraformGenerator
Make sure that you have installed the latest version of [TerraformGenerator].  
To do that, stop your server and upload the jar file to the `plugins` directory of your server. Afterwards, can you start your server again.

Please note that some server types like CraftBukkit may not work with TerraformGenerator and can result in a crash of your server.  
To prevent this do we recommend the usage of either Spigot or PaperMC (The latter one is more recommended).

## Step two: Create the world
You can choose between two methods on how to generate the world with TerraformGenerator

### Method One

1. Turn off the server if it is running
2. Open the `bukkit.yml` and add the following info to it.  
   ```yaml
   #
   # NOTE:
   # This section does by default NOT exist in your bukkit.yml
   # You have to add it yourself.
   #
   worlds:
       <world_name>: # Replace <world_name> with the world name you want to use.
           generator: TerraformGenerator
   ```
3. If present delete the folder of the world that you want TerraformGenerator to create.
4. Start your Server again.

### Method two

*This method requires a World-Management plugin to be installed and enabled on your server.  
*Multiverse has been known to cause a few weird issues. Follow the instructions very precisely.*
In our example will we use Multiverse-Core. Terraform Generator may work with other World-managers but we won't guarantee it!*

1. **Make sure you did the steps of the [first method](#method-one) before you continue.**
2. Make sure that the World-Manager is enabled (Shows up green in the `/plugins` list).
3. When a World with your selected name already exists, delete it with `/mvdelete <world>` followed by `/mvconfirm`
   - Note that this won't work with default worlds and requires a stop of your server and manual deletion of the world!
4. Create the world using `/mvcreate <world> normal -g TerraformGenerator` where `<world>` is the name of the world you defined in [the first method](#method-one)

## Step three: Pre-generate the world (Optional)
It's recommended but not necessary to pre-generate your world using a plugin.  
Please take a look at our [[FAQ|FAQ#pregenerating the world]] for a list of plugins for pre-generating Worlds.