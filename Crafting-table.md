Crafting table is a special mechanism that allows to exchange items between player and virtual vendor. You can use this mechanism to add RPG element of creating powerful gear and weapons out of some junk was dropped by enemies. 

Crafting table consist out of crafting recipes which describe the trading, i.e. input items get traded to output items.

Crafting tables can be managed in [Mappet dashboard](./Mappet-dashboard). The first panel in the left sidebar opens crafting tables editor.

## Editing

Once you pick or create a crafting table, you'd see an editor like this:

![Crafting table editor](https://i.imgur.com/sTCe9mj.png)

### Crafting table's title

In the **Crafting table's title** you can choose a title that will be displayed in a crafting screen that is opened via `/mp crafting open` [command](./Commands). It's not used in the dialogue screens.

### Crafting recipe management

On the left from the main editing area, there is a recipe list. There you can pick and manage recipes. If you right click anywhere in that area, a context menu will appear with options to **add** a new crafting recipe and **remove** currently selected recipe.

Additionally, you can also manually **change the order of recipes by drag-and-dropping** recipe's title in the list to the desired place in the list.

Once you have picked, or created a crafting recipe in the sidebar, you can edit the recipe.

### Recipe's title

Recipe's title allows to give a description to the crafting recipe. Quite self-explanatory.

### Ingredients and Result

These two modules allow to add item stacks that will be used for the crafting recipe. Ingredients are one or more item stacks that will be taken from player during the crafting exchange, while result items is the item stacks that will be given to the player in exchange.

If ingredients aren't present, or they are of insufficient count, then player won't be able to perform the exchange.

#### Managing items

In both modules, you can click on the ➕ icon to add an item stack slot. There you can pick the item stack from your inventory. If you want to remove the item stack from either ingredients or result, simply right click on the stack, and click on ➖ **Remove item** item.

### Expression condition

In expression condition you can type in an [expression](./Expressions) that allows you to hide the crafting recipe from the crafting recipe list.

### Crafting hotkey

