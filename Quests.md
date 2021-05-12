Quests is a mechanism for to make players do something for a reward. You can use this mechanism to either reward player with cool loot, or immerse players into the lore through stories using quest chains.

Players can view currently taken quests in the player journal (`J` key by default) screen, quests can be taken and completed either through [dialogues](./Dialogues) and [quest chains](./Quest-chains) and `/mp quest` [subcommands](./Commands#quest-commands).

Quests can be managed in [Mappet dashboard](./Mappet-dashboard). The second panel in the left sidebar opens quest editor.

## Editing

Once you pick or create a quest, you'd see an editor like this:

![Quest editor](https://i.imgur.com/D4sDyQ1.png)

### Quest's title and description

Those two are self explanatory, they are quest's title and description. Title allows you to summarize the quest's gist in a couple of words, while the description allows you to dive deeper into the details of the quest like providing the details of where, what, who and etc. 

They will appear somewhat like this in the dialogue quests view:

![Quests](https://i.imgur.com/wkDLz7Q.png)

#### Description's formatting

Within description field you can use some simple formatting. Inputting `\n` counts as a newline, so if you want to start a new paragraph, you'll need two newline breaks like `\n\n`.

You can also use `[` as a substitute to `§` (section) symbol to do color formatting as described in Minecraft wiki's [Formatting codes](https://minecraft.fandom.com/wiki/Formatting_codes) page.

**Note**: these are true at the moment of current alpha.

### Cancelable 

Cancelable toggle determines whether quest can be declined by the player in the player journal. If the quest is not cancelable, then the decline button will be unclickable:

![Decline button is grayed out](https://i.imgur.com/mcmf7Mi.png)

### Objectives

Objectives are the goals that you give to the player that determine what player must do to complete the quest. At the moment, there are following objectives present in the mod:

* **Kill objective**, this objective tells player to slay a specific amount of mobs
* **Collect objective**, this objective tells player to acquire specific item

You can add objectives by pressing ➕ icon to the right of the **Objectives** label. After clicking it, a context menu will popup and you'd be able to select the objective you want to add. If you want to remove an objective, you can right click on its area, and pick the ➖ **Remove this objective** context menu item.

### Kill objective

Kill objective have multiple fields that you need to worry about. Those are: Entity ID, Count and Matching NBT.

The button under **Entity** label opens an overlay modal that contains a list of all available entities in the game. For example, if you'll pick `minecraft:pig`, player will need to kill a pig. **Keep in mind** that not all entities are killable, meaning that you won't be able to kill entities like boats, item frames, etc, so test the quest if you have doubts.

The field under **Count** determines how many entities matching by the Entity ID and Matching NBT (if it's present) needed to be killed to consider given objective complete.

And finally text field under **Matching NBT** label allows to input additional NBT data that will be compared against the killed entity. For example:

* If you want to target a baby zombie, you'd need to specify `minecraft:zombie` in the entity ID picker and `{IsBaby:1b}` into the **Matching NBT** field.
* If you want to target a Mappet NPC with `test` NPC ID, you'd need to specify `mappet:npc` in the entity ID picker and `{NpcId:"test"}` into the **Matching NBT** field.

**ProTip™**: if you want to figure out the Matching NBT tag, the best way to find the variables is to kill that specific mob, pick up its morph, and inspect its NBT data, which you can do it in the morph editor.

### Collect objective

Collect objective have only one field which is an item slot, simply click on the slot, and pick the item. Then player will have to collect this specific item, and as many as it says in the bottom right corner of the item stack.

Keep in mind that if you have custom NBT data on the tag, the player will have to collect exact this item, however the damage (how much item is damaged) of the item doesn't get accounted.

### Triggers

And finally, the the last quest options are accept, decline and complete [triggers](./Trigger). 

As the names state, these individual triggers will be triggered when player accepts a quest that was given to them via the `/mp quest accept` command or they accept it from a dialogue, declined it through the `/mp quest decline` command or from the player journal, or completed the quest through the `/mp quest complete` command or via a dialogue.

## Mechanics

It worth noting that there is one special mechanic that you need to know about quests. 

**Once a quest is completed by a player** a `1` will be added to both global and that specific player's state by key `quests.QUEST_ID`. So if I completed a quest by ID `mchorse.intro`, then to both `~` and my player states a `1` will be added to the key `quests.mchorse.intro` (you can verify that by completing a quest and executing `/mp print ~` and `/mp print YOUR_USERNAME`).