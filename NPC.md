NPCs are Mappet entities that can be used for plethora of things. They can be traders, conversers, quest providers, companions, foes, bosses and etc. You can do so many things with them it's impossible to list all uses. NPCs utilize morphs which grants you freedom of being able to make them look like whatever you want them to look like.

NPCs can be spawned by `/mp npc summon` command, or by using the NPC tool, and edited using `/mp npc` [commands](https://github.com/mchorse/mappet/wiki/Commands#mp-npc-state-target-state) or using NPC tool.

NPCs can be managed in [Mappet dashboard](./Mappet-dashboard). The third panel in the left sidebar opens NPC editor.

## Editing

Once you pick or create an NPC, you'd see an editor like this:

![NPC editor](https://i.imgur.com/mDe1NQt.png)

There you can edit NPC's states and individual state options. In this editor, you're essentially creating and configuring NPC blueprints for their behavior. 

### Main options

Here is the description of what main options on the top do:

* **Path finding distance** allows to setup the maximum path distance which the NPC will use to traverse and find targets the world. The higher the number the more CPU resources it will use.
* **Unique** (**not used yet**) will allow to make the NPC unique, meaning server will take care of its spawning so that there wouldn't be a possibility for incidents.

### States

On the left from the main property editor you can see the states list. These allow you to create different variants of the same NPC and later on change them using `/mp npc state` [command](./Commands#mp-npc-state-target-state). Same way as in other places within Mappet, you can right click on the list to add and remove states, and click on the list items to pick a state to edit.

`default` is the default state name that is used in Mappet when you omit the state.

### Options

Here is the breakdown of all options:

#### General options

* **Faction** the ID of the faction that NPC will belong to.
* **NPC's morph** the morph that NPC will use.
* **NPC drops** allows to setup items that will be dropped from NPC upon death. ➕ adds a drop, there you can add an item stack and drop chance from `0` to `100`. You can right click on the drop to show context menu and remove it.
* **XP drop** allows to setup amount of XP an entity will drop. For more information about how much do you want the NPC to drop experience, see [this page](https://minecraft.fandom.com/wiki/Experience#Experience_amounts_by_source).

#### Health options

* **Max HP** determines how many health points will NPC have. `2` is a full heart (`20` is player's default health).
* **Initial HP** determines how many health points will NPC have upon spawning. Naturally, it can't be greater than **Max HP**.
* **HP regeneration delay** determines how many ticks (`20` ticks = `1` second) should pass until the NPC will start regenerating one heart (i.e. after getting hit).
* **HP regeneration frequency** determines after how many ticks every heart will be regenerated.

#### Damage

* **Damage** determines how many hearts (without armor) NPC will deal upon hitting an enemy.
* **Fall damage** determines whether NPC can get damaged by fall damage.
* **Fire damage** determines whether NPC can get damaged by fire damage.
* **Invincible** determines whether NPC can get damaged at all.
* **Killable** determines whether NPC can be killed. This makes NPC only killable by the `/kill` command. The health is still can be depleted to a value that is close to `0`.

#### Movement

* **Speed** determines how fast NPC walks, chases targets, patrols, etc. `1` is default Minecraft player walking speed.
* **Can swim** determines whether an NPC can float on the water.
* **Has a post** toggles the post logic. When enabled, NPC will be returning to the block position specified under the toggle. The field underneath block position is the post's radius where NPC can safely wonder around until returning back to the post.
* **Patrol points** under patrol points you can setup patrolling for the NPC. ➕ on the right of the label allows to add a point. When adding a point it will use player's current position. You can remove the point by right clicking and ➖ **Remove block position**.
* **Circulate patrol** allows to toggle whether NPC should return to the first point instead of going backward. So let's say we have 3 points. With the option disabled, the NPC will be patrolling 1, 2, 3, 2, 1, 2, 3, etc., while with circulate patrol enabled, the NPC will be patrolling like 1, 2, 3, 1, 2, 3, etc.
* **Follow target** allows to input username or `@r` for random of a player which NPC should follow.

#### Behavior

* **Look at player** whether NPC will be looking at a player
* **Look around** whether NPC will be looking around in the idle state
* **Wander** whether NPC will randomly wander around
* And finally there you have lots of [triggers](./Trigger) for:
    * **On NPC initialization** which gets triggered upon NPCs summoning via a command or NPC tool.
    * **On NPC interaction** which gets triggered upon player right clicking the NPC.
    * **On NPC damaged** which gets triggered when an NPC gets hurt.
    * **On NPC death** which gets triggered when an NPC dies.
    * **On NPC tick** which gets triggered every tick when an NPC exists.
    * **On NPC target** (**not used yet**) which will be used when an NPC targets an entity


## NPC tool

NPC tool is an item in Mappet's creative item tab which allows to simplify NPC spawning and editing.

![NPC tool](https://i.imgur.com/QV5SpBn.png)

First, when you grab a brand new tool from the creative tabs, you need to configure the tool by and right clicking while sneaking (holding `Shift` key). A menu like this will appear: 

![NPC tool screen](https://i.imgur.com/3h7vdTe.png)

There you can pick the NPC's ID you want to spawn and its state. Once you picked the ID and state, you can close the menu, and right click on the ground to spawn an NPC by that ID and state. 

Beside that, you can also edit individual NPC's properties just like in the NPC editor:

![Individual NPC editor](https://i.imgur.com/Ubct0va.png)

Once you'll close the menu, the NPC will get updated.
