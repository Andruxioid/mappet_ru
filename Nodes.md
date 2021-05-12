Node system is a powerful feature that is used by [events](./Events), [dialogues](./Dialogues) and [quest chains](./Quest-chains) features to represent complex relationship between nodes.

Here is an example of an event that represent a very primitive **dirt or diamonds** lootbox system:

![Lootbox](https://i.imgur.com/E6IKVPI.png)

## Getting started

### Adding and removing nodes

Let's say you created a new event called `new` in the event editor. The first step to start working with nodes is to either right click on the editor and add a single node of your choice, or press one of the Ctrl + *Number* keybind to add a node (see available node adding keybinds in `F9` menu).

![Add a node](https://i.imgur.com/A5iJmJf.png)

Once the node was added it will be selected, and you can edit its fields in the bottom left corner of the node editor. Now, create a couple of more nodes, like 5 of them. Once you're comfortable with creation of nodes, try removing a node. To remove a node, click on it, then right click anywhere and click on ➖ **Remove selected nodes** context menu item.

### Selecting, tying and untying nodes

Cool, now you have all those nodes by themselves. The main feature of nodes is their ability to being tied to another nodes. To tie two nodes together, first select (by clicking) the input node, in which the output node will be flowing, which is usually the bottom node, and then add the top output node (by clicking on a node while holding `Shift` key). Alternatively, you can select multiple nodes by click dragging while holding shift:

![Box selection](https://i.imgur.com/MTtUI8j.png)

Once two nodes are selected, ensure that the top node has lighter blue selection color, and if it's not then Shift click on it again, and either press `F` to connect, or right click and **Tie selected**. Then the nodes will be connected:

![Connected nodes](https://i.imgur.com/R8UmQHs.png)

Great! As you can see based on the node connection flow animation, the bottom node is being the input node, because the flow animation circulates into the direction of the input node, and the top node is the output node. If you want to untie these two nodes, what you have to do is to select again first the bottom node, and then the top node, and either press `U` to unconnect, or right click and **Untie selected**.

**Note**: nodes an be connected circularly, however **no node can be tied to itself**.

### Marking the node as main

In [event](./Events) and [dialogue](./Dialogues) node systems, you have to specify a main node, that's the node from which the entire execution flow starts. To mark a node as a main simply select a node (by clicking it) and press `M` on the keyboard. That will mark the node as main, and it will have this arrow down icon:

![Main node](https://i.imgur.com/ycAr4CK.png)