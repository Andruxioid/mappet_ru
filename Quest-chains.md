Quest chains is a special data type that uses the node system (more about node system can be found on [nodes](./Nodes) page) to represent quest progression. Quest chains are used within [dialogue system](./Dialogues) to provide [quests](./Quests) out of the dialogue.

Quest chains can be managed in [Mappet dashboard](./Mappet-dashboard). The last panel in the left sidebar opens quest chain editor.

## Editing

Once you pick or create a quest chain, you'd see an editor like this:

![Quest chain editor](https://i.imgur.com/xaR0gwu.png)

It works just like the node editor for dialogue and nodes, however, it provides only a single type of node in its system, and it's the quest node.

### Quest node

Once you select a quest node. Beside the common **Title** field, there are also three fields:

* **Quest** field determines the quest by the given ID that will be used to display in the dialogue
* **Quest giver** is the ID of an NPC, `[subject_id]` if the dialogue shown through `/mp dialogue open` [command](https://github.com/mchorse/mappet/wiki/Commands#mp-dialogue-open-target-id-subject_id), which will give quest, meaning you would be able to see the quest only if the NPC or the `[subject_id]` matches **Quest giver**
* **Quest receiver** same thing as **Quest giver** but for completing quests, i.e. which NPC/`[subject_id]` allows to hand in the completed quest

### Hierarchy

The way you specify the quest chain's progression is by connecting existing nodes. Nodes that don't have input connection (top connection) are the quest chain starters, they are the first quest in the chain, while connected quest chain down the line are comes after you completed the quest up the chain.

Consider following:

![Quest chain example](https://i.imgur.com/FFei6X0.png)

In both cases those chains will certainly will work, however, the left chain is more readable and intuitive than the right chain. 

* The left chain reads as: complete `da`, then `test_nbt` and then `test`, and it works this way.
* The right chain reads as: complete `easy`, then `example`, and then `quest`, **HOWEVER** instead it actually going to work like `quest`, then `example` and finally `easy`!

So when tying these quest nodes, make sure to select **first the bottom node**, and then the top node, and tie only after you selected in that order.