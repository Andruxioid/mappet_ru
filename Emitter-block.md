Emitter is a Mappet block which emits redstone signal, when given expression evaluates a non-zero value (i.e. not a `0`). It could be used to connect Mappet's [expressions](./Expressions) with redstone contraptions, for example:

* Open a redstone door upon completion of a specific quest
* Extend a platform (using a piston) for parkour when player holds a specific item
* Repeat some command block command by using world time every *X* ticks, etc.

You can acquire an emitter block in Mappet's creative item tab.

![Emitter block](https://i.imgur.com/fAZNtpj.png)

## Configuration

To configure an emitter block, place it down somewhere, and right click it. You'll see following screen:

![Emitter block's configuration screen](https://i.imgur.com/7bVWN3T.png)

### Expression

**Expression** field allows to input an [expression](./Expressions) that will be executed every 5 ticks (`0.25` seconds). If the given expression evaluates to `0`, then the block won't emit any redstone signal. Otherwise if it evaluates to any value other than `0`, then it will emit redstone signal.

### Radius

**Radius** field allows to configure distance upon which it will execute its expression. If one ore more players are within the distance of the emitter block, then it will update its signal depending upon expression. If there are no players within its radius, then it won't update its redstone signal.