# HuskyCrates
[![Build Status](http://ci.communitybuilt.net/job/HuskyCrates/badge/icon)](http://ci.communitybuilt.net/job/HuskyCrates/) [![Paypal donate](https://img.shields.io/badge/paypal-donate-yellow.svg)](https://www.paypal.me/KasperFranz/)

A simple, straightforward crate system for Sponge!

This fork has some changes made to it  - this is updated with the documentation for it :)!
You can download development builds from my [CI server](http://ci.communitybuilt.net/job/HuskyCrates/) where it is always up to date with the latest code.

## Changes made to this fork.:
 - Implemented the option to use meta IDs.
 - Using a poppy instead of a nether star
 - Send the gifts to the enderChest if their inventory is full.
 - Performance changes
 - ~Changed format of the commands for getting keys/chests to be `/crate key <crate id>` and `/crate <crate id>` instead of `/crate <crate id> chest/key`, this is making it way easier to manage internally.~  (this was made as a PR to @codeHusky)
 - ~Possible to change the colors in the crate.~ (this was later implemented in the main branch by @CodeHusky)
 - ~Possible to add quantity parameter to the key and chest commands~ (this was made as a PR to @codeHusky)

# Config
HuskyCrates might not create a config automatically for itself, so make sure to make one if it doesn't.

**config > huskycrates > huskycrates.conf**

To configure crates, here's a basic crate to get you started.

```
crates {
    commandcrate { # This line represents the crate id.
        items=[
            {
                amount=1 # The amount of an item.
                chance=50 # The chance, out of 100, that this item will be drawn.
                command="give %p minecraft:diamond 10" # A command to run on picking this item.
                id="minecraft:diamond" # The id of the item we're using
                meta=0 #If there is meta on your item this is a good option to use it!
                name="Diamond Box" # A name
            },
            {
                amount=24
                # Chances are assumed for items that don't have it.
                id="minecraft:dirt"
                lore="Literally dirt. :)" # Lore.
                name=Dirt
                meta=0 #If there is meta on your item this is a good option to use it!
                #Enchanted dirt coming soon.
            }
            #Make sure your chances don't add past 100 or you'll get an error!
        ]
        name="§3Command Crate" # Make sure this looks good everywhere :)
        color1="000000"  #Color 1 of the particles going around the crate.
        color2="ff8b29"  #Color 2 of the particles going around the crate.
        type=Spinner # Types will be added in the future, but keeping this as a Spinner will keep your config future proof.
    }
    #Keys will also be configurable in the future, so keep your eye out.
}
```
Please note that if you want a chance maximum other than 100 right now, you cannot have any assumed chances. Make sure your numbers work out in the end.

# Commands
- `/crate` - does nothing
- `/crate reload` - Reload your configuration
- `/crate crate <crate id> [quantity]` - Gives you a placeable crate block. Will look weird but trust me, it's the right thing.
- `/crate key <crate id> [player]` - Give you, or someone you choose, a crate key.

Crate IDs are the values you put first inside of the crates{} in the config. So like, command in the example would be the crate id.

# Permissions
- `huskycrates.tester` - Allows a user to override the key removal in the inventory.
- `huskycrates.reload` - Reload the configuration.
- `huskycrates` - Gives access to the `/crate` command.

**Permissions To Be Implemented**
- `huskycrates.<crate id>.use` - Allows a user to use a certain crate
- `huskycrates.<crate id>.create` - Allows a user to get a certain crate's item
- `huskycrates.<crate id>.key` - Allows a user to spawn a certain key for themselves
- `huskycrates.<crate id>.key.other` - Allows a user to spawn a certain key for others.
