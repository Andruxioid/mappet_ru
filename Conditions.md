Conditions is a Mappet mechanism that allows to check something, kind of like [expressions](./Expressions) do, but using GUI and different condition blocks. If you're not good with coding, you may try using conditions instead of expressions.

Conditions are available in every [checker](./Checker) component.

## Mechanics

Conditions can have multiple condition blocks, which examine the current context and return a boolean value (which basically means yes or no, on or off, positive or negative, `true` or `false`, `1` or `0`). 

Condition goes over those blocks and evaluate them one by one from **top to bottom**. By default if all blocks return a positive then condition works and enables whatever it should've enabled (for example enabling redstone signal in an [emitter](./Emitter-block)). Individual blocks can be inverted or compared using OR (meaning instead comparing using OR instead of AND), and even nested by using [condition](./Conditions#condition-block) block.

### Demonstration

Let's say we have following condition:

![Simple condition](https://i.imgur.com/o9cT6dH.png)

By default, this will read as: if player "Holds a Grass Block" **and** "Is day?" Only in case when all of these conditions are **true**, i.e. the player is actually holding a block and it's day (the world time is between `0` and `12000`).

This scenario can be summarized by following table:

|Block|Result|
|-|-|
|Holds Grass Block|`true`|
|Is day?|`true`|

But once one of those becomes `false`, for example player stops holding a grass block, then the condition will return a negative result. But, if you want the player to hold grass block or it should be day, in that case you'll need to mark "Is day?" block as OR like this:

![Marking as OR](https://i.imgur.com/ZOHJIyR.png)

Then the condition will send a positive result either, if the player will hold a grass block, or it's day. It will read as: if player "Holds a Grass Block" **or** "Is day?" The ❗ allows to invert the result returned by a block, so if we'll go to "Holds Grass Block" block and enable inversion:

![Marking as NOT](https://i.imgur.com/vUtvBsH.png)

Then the condition will read as: if player **not** "Holds a Grass Block" **or** "Is day?" So the emitter will emit the redstone signal, if the player doesn't hold a grass block, or it's day. If you'll add into this nested conditions, it will get even more crazier. What I would recommend in such situations is *reading* those blocks out loud, and seeing if it makes sense.

## Editing

When a checker component is toggled in a condition state (when **Edit condition...** button is present) click on the **Edit condition...** button and it will open condition editor modal:

![Empty condition editor](https://i.imgur.com/jEvG8cJ.png)

By right clicking where it says **Right click here...** and **Add a condition...** will allow you to add a condition. Try adding a World time condition block. After adding the block, on the left you will see condition block list, and on the right the condition block editor.

![Condition editor](https://i.imgur.com/mzJFtFx.png)

By right clicking you can also remove and copy/paste conditions. If you have multiple condition blocks in the list, you can also sort them by drag and dropping.

### Condition blocks

At the moment of writing of this documentation, condition editor supports following condition blocks:

* **Quest** block, this block allows to check whether player(s) (or the world) has no quests in-progress or completed (i.e. absent), in-progress quests or completed [quests](./Quetst).
* **State** block, this block allows to compare a [state](./States) of a player or of the world.
* **Dialogue** block, this block allows to check whether a player read a [dialogue](./Dialogues).
* **Faction** block, this block allows to check player's relationship with a [faction](./Factions).
* **Item** block, this block allows to check whether a player holds, equips or has an item in the inventory.
* **World time** block, this block allows to check world's time.
* **Condition** block, this block allows to setup nested conditions.

Every condition block has two icon buttons similar to ❗ and 🔀 emojis. ❗ allows you to inverse the result of the block, while 🔀 allows you to mark the block to be combined with previous result using OR instead of AND.

### Quest block

In a quest block, you can pick [quest](./Quests)'s ID, the completion state (absent, present or completed) and the target player (see below for more information about [target](./Conditions#targeting)).

### State block

In a state block, you can pick the key of a [state](./States), target where to look for the state (see below for more information about [target](./Conditions#targeting)) and comparison mode (see below for more information about [comparison modes](./Conditions#comparison)).

### Dialogue block

In a dialogue block, you can pick [dialogue](./Dialogues)'s ID, the [marker ID](./Dialogues#dialogue-reading) and the target player (see below for more information about [target](./Conditions#targeting)).

### Faction block

In a faction block, you can pick [faction](./Factions)'s ID, faction comparison mode, the target player (see below for more information about [target](./Conditions#targeting)) and comparison mode (see below for more information about [comparison modes](./Conditions#comparison))

Faction comparison mode can be:

* **Aggressive** checks whether attitude towards found player is aggressive.
* **Passive** checks whether attitude towards found player is passive.
* **Friendly** checks whether attitude towards found player is friendly.
* **Score** checks faction scare of the found player using [comparison mode](./Conditions#comparison).

### Item block

In an item block, you can pick any item stack, item comparison mode and the target player (see below for more information about [target](./Conditions#targeting)).

Item comparison mode can be:

* **Held (hands)** checks whether the player must hold in hands (stack count isn't accounted for).
* **Equipment (armor)** checks whether the player has an item stack equipped in an armor slot (i.e. helmet, chestplate, leggings or feet).
* **Inventory** checks whether the player has an item stack in the inventory.

### World time block

In a world time block, you can pick time condition mode, and range (but only if time condition range is **Range**).

Time condition mode can be:

* **Is day?** checks whether it's day in the world (`0` — `12000`).
* **Is night?** checks whether it's night in the world (`12000` — `24000`).
* **Range** checks whether world's time is between minimum (the left field) and maximum (the right field).

### Condition block

In a condition time block, you can edit the nested condition by clicking **Edit condition...** button which will open another condition editor on top of current condition editor. There you can edit conditions.

## Targeting

In most condition block editors, there is Target button which allows to toggle between different targeting modes.

* **Global** targets the world/server.
* **Subject** targets the subject entity in [event's context](./Events#event-context).
* **Object** targets the object entity in [event's context](./Events#event-context).
* **Selector** targets one player by given [target selector](https://minecraft.fandom.com/wiki/Commands) (if target selector finds more than one player it return voids the check of the block).

## Comparison

In some condition block editors, there is Comparison module which allows setup comparison of `found` value. The value field allows to set the `target` value against which the comparison will be evaluated. Consider that `found` and `target` are variables, then comparison operators will work like this:

* `found <  target` (`<`), true if `found` is less than `target`
* `found <= target` (`<=`), true if `found` is less than or equals to `target`
* `found == target` (`==`), true if `found` equals to `target`
* `found >= target` (`>=`), true if `found` is greater than or equals to `target`
* `found >  target` (`>`), true if `found` is greater than `target`