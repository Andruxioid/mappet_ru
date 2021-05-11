Trigger is a Mappet block which allows to add [triggers](./Trigger) for when a player left or right clicks on the block. Trigger block can be used for variety of things:

* Open a dialogue for a player to inspect some kind of item lying on the floor (let's say inspect a skull)
* Open a dialogue with a crafting table (this will create an immersion of a workbench)
* Execute an event which will open a secret door
* Decorative block that upon hitting will be doing some sound (like a bell), etc.

You can acquire a trigger block in Mappet's creative item tab.

![Trigger block](https://i.imgur.com/I4IoHI6.png)

### Finding a trigger block

Since trigger blocks are non solid invisible blocks, it might be hard to find them when creating a map. However, you can see the locations of trigger blocks (yellow cubes) when F3 debug screen is enabled.

This **works only in creative** mode.

![Trigger block in F3 debug screen](https://i.imgur.com/7Sthny0.png)

## Configuration

To configure a trigger block, place it down somewhere, and right click it. You'll see following screen:

![Trigger block's configuration screen](https://i.imgur.com/42o2JOZ.png)

### Left and right click triggers

Left and right click [triggers](./Trigger) allow to setup a trigger which will be executed upon player left clicking and right clicking the block.

In creative mode, however, you **can't test left** click trigger (you'll need to change to survival or adventure mode), because it will break the block. However you can test right click trigger by **sneaking and right clicking** the block.

## Collidable

Collidable toggle allows to toggle trigger block's bounding box, meaning you can make trigger block behave like a barrier block.