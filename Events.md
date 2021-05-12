Events are basically programmable [node systems](./Nodes) that allows you to program logic for your adventure maps without writing any scripts or code. The way it works is you have multiple types of nodes at your disposal that you can create logic with them. Connecting these nodes together can produce a meaningful *program* that can do something with the world, player, NPCs and etc.

Events can be triggered either from [triggers](./Trigger) or via `/mp event trigger` [command](https://github.com/mchorse/mappet/wiki/Commands#event-commands).

Events can be managed in [Mappet dashboard](./Mappet-dashboard). The third panel in the left sidebar opens event editor.

## Editing

Once you pick or create an event, you'd see an editor like this:

![Node editor](https://i.imgur.com/A5iJmJf.png)

Event system supports following types of nodes:

* **Command** node allows to execute commands, and depending on the result of command execution direct the flow
* **Condition** node allows to check an [expression](./Expressions), and depending on the evaluated result of the expression direct the flow
* **Switch** node allows to direct the execution flow depending on the output of the given [expression](./Expressions)
* **Timer** node allows to delay the execution

### Command node

Command node executes a command from the perspective of the subject that triggered it. The subject could be a player, if the event was triggered through `/mp event trigger`, trigger block, or a region block, or an [NPC](./NPCs) if it was triggered from one of the NPC triggers.

Beside that, commands within command node can use special formatting to evaluate an [expression](./Expressions) within `${...}`. For example, if you want to use `/setblock` command to put a block, however, you want it to place a fire block during the night, but stone block during the day. To do that, you can simply input following command:

```
/setblock -1514 4 1981 minecraft:${world_is_day() ? "stone" : "fire"}
```

And it will replace the `${world_is_day() ? "stone" : "fire"}` depending on what time of the day it is. I.e. fire during the night, and stone during the day. Also, if you ever need to reference the subject player/NPC in commands, you can use `${subject}` expression (which is UUID of the subject entity) which works with all commands that provide target selector arguments.

When command gets executed, if there was no error, then it will pass the execution to all of its input (child) nodes. However, if the command errored, then it will won't continue the execution. **Binary** toggle allows to change this behavior. Instead of all on success, or none on failure, binary instead works like this: on success it will pass the execution to the first node (denoted by `0` and green flow), while on error it will pass the execution to the second node (denoted by `1` and red flow). All other connected nodes will be **ignored** (as depicted by node `2` with yellow semitransparent flow).

![Binary mode in action](https://i.imgur.com/cdrc8bU.png)

### Condition node

Condition node evaluates its [expression](./Expressions), and depending on the resulted value it will pass the execution. If the resulted value is a non-zero (anything but `0`) then it will execute all of its connected input (child) nodes. If the expression evaluates to `0`, then no nodes will be executed. Same as with command node, **Binary** toggle allows to change the behavior from all-or-none execution to first-or-second node.

Using binary, you can create `if-elseif-else` like this:

![if-elseif-else execution](https://i.imgur.com/LN7FpUq.png)

### Switch node

Switch node is similar to condition node, but instead of passing execution using either to all-or-none or binary model, it instead evaluates its [expression](./Expressions) and passes the execution to the child node at index of the resulted value. For example, let's say you want to randomly pass the execution to one of 3 command nodes. This can be achieved by inputting `floor(random(0, 3))` into the switch node, and you get something like this:

![Random execution](https://i.imgur.com/xbnrp9B.png)

### Timer node

Timer node allows to delay the execution of the node system by given amount of ticks. If you want to execute some commands gradually, you can use this node to delay commands.

## Hierarchy

There are no restriction to the hierarchy, or how the nodes should be arranged in a specific order, however, for the event node to start, you need to specify the main node as described [on the Nodes](https://github.com/mchorse/mappet/wiki/Nodes#marking-the-node-as-main) page.

## Passing custom data

`/mp event trigger` [command](./Commands#mp-event-trigger-target-id-data) has an optional argument called `[data]`. There you can pass some arbitrary NBT data which can be used within the event. For example, let's say I have a Switch node somewhere within the event that I want to control from outside, something like this:

![Custom variable](https://i.imgur.com/ORa6Z5O.png)

So now, I can pass that variable using the last argument through NBT like this:

```
/mp event trigger @r fire {input:2}
```

This particular command will pass the `input` with value of `2`, and according to the switch node, it will pass the execution to the node at index `2` (the most right). You can input only numerical and string values into `[data]`. Compound and list tags **are not supported**!