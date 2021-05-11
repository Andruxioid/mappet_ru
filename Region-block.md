Region is a Mappet block which allows to add [triggers](./Trigger) to when a player enters or exits the region, configured by the block. It also can be used to disallow players from entering the region. Region blocks can be used for variety of things:

* Start the arena when player steps into the middle of the arena
* Complete a quest upon entering the region
* Delayed death traps
* Activating a Blockbuster scene upon entering the region

You can acquire a region block in Mappet's creative item tab.

![Region block](https://i.imgur.com/emuK3YS.png)

### Finding a trigger block

Since region blocks are non solid invisible blocks, it might be hard to find them when creating a map. However, you can see the locations of region blocks (purple blocks) when F3 debug screen is enabled. Additionally, in F3 the volume of the region is displayed as well.

This **works only in creative** mode.

## Configuration

To configure a region block, place it down somewhere, and right click it. You'll see following screen:

![Region block editing panel](https://i.imgur.com/rZV6N3Q.png)

### Passable

When disabled, this option allows to make it so player can't enter the region. It will teleport back the player to last position out of the region. Enabled expression allows to control whether players can pass or not (any expression that evaluates to `0` will disable teleportation).

Also when disabled, on enter and on exit triggers, and trigger delay **won't be used**.

**Note**: at the moment of alpha, this option can sometimes result into player teleporting on the other side of the region. It's a bug.

### Enabled expression 

Enabled expression allows to provide an [expression](./Expressions) that will enable execution of triggers if the evaluated value is a non-zero value, or if it's empty.

### Trigger delay

Trigger delay allows to delay the execution of on player enter trigger by provided amount of ticks (there are `20` ticks in a second). It won't affect the on player exit trigger, it will get executed immediately after player exited the region.

This option doesn't work when passable option is disabled. 

### Shape

Shapes component allows to configure the shape of the region. You can switch the shape by left or right clicking on the button under **Shape** label. At the moment, region block supports following shapes:

* Box
* Sphere
* Cylinder

Each of these are self explanatory, and they have pretty similar properties. The property they have in common is XYZ offset, which allows you to shift the region by specific amount of blocks. This should allow you to hide region blocks within walls or underground, while having region itself where you want it to be.

#### Half size

Box's half size allows you to specify the size of the region's box on X, Y and Z axes. Keep in mind that the full size of the box is twice as what you'll input into the field.

#### Radius and height

Cylinder's radius and height allows you to change the horizontal radius of the cylinder and its height, respectively. As with box's half size, both radius and height are calculated relative to the offset point so they are half of the size.

#### Ellipsoid radius

Sphere's ellipsoid radius allows you to change the horizontal radius of the sphere and its vertical radius, respectively. As with box's half size, both radii are calculated relative to the offset point so they are half of the size.