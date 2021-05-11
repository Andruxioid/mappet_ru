Mappet provides a lot of commands to work with its features. This page lists all commands that are available in the mod. `/mp` is the main command that provides many subcommands to work with specific features.

## State commands

`/mp state` command provides subcommands that allows to modify [states](./States). `<target>` can be either a target selector that points out to a  unique player (it could also be a username or UUID), or `~` which stand for server's global states.

### `/mp state add <target> <id> <expression>`

Adds some value to `<id>` state.

### `/mp state clear <target> <id>`

Removes the `<id>` state from the system.

### `/mp state if <target> <id> <expression>`

Checks whether `<id>` state is equal to `<expression>`, if it's not then command will error, otherwise nothing will happen.

### `/mp state print <target>`

Outputs into the chat all the states that `<target>` stores.

### `/mp state set <target> <id> <expression>`

Sets the exact value to `<id>` state.

### `/mp state sub <target> <id> <expression>`

Subtracts some value from `<id>` state.

## Dialogue commands

`/mp dialogue` command provides subcommand to work with [dialogues](./Dialogues).

### `/mp dialogue open <target> <id> [subject_id]`

Opens a dialogue by given `<id>` for player(s) found by `<target>` selector. `[subject_id]` allows to change the subject's ID which is used by quest chains to give and receive quests.

## Crafting commands

`/mp crafting` command provides subcommands to work with [crafting tables](./Crafting-tables):

### `/mp crafting open <target> <id>`

Opens a crafting table by given `<id>` to player(s) by `<target>` selector.

### `/mp crafting drop <id> [index] [x] [y] [z] [mx] [my] [mz]`

Drops an item in the world at `[index]` from crafting table by `<id>` at given XYZ, relative offset `~` is supported. If `[index]` omitted or inputted as `@r` will drop a random item. `[mx]`, `[my]` and `[mz]` can be used to set initial item(s)' velocity.

## Event commands

`/mp event` command provides a subcommand to work with [events](./Events):

### `/mp event trigger <target> <id> [data]`

Triggers an event by `<id>` with additional context in form of player(s) found using `<target>` selector. Additional NBT `[data]` can be sent to the event execution.

## Quest commands

`/mp quest` command provides subcommands to work with [quests](./Quests):

### `/mp quest accept <target> <id>`

Makes player(s) by `<target>` selector take quest by `<id>`.

### `/mp quest decline <target> <id>`

Makes player(s) by `<target>` selector decline quest by `<id>`.

### `/mp quest complete <target> <id>`

Makes player(s) by `<target>` selector complete quest by `<id>` regardless of whether goals were finished.

## NPC commands

`/mp npc` command provides subcommands to work with [NPCs](./NPCs):

### `/mp npc summon <id> [state] [x] [y] [z]`

Spawns an NPC with given `[state]` (if omitted it's `default`), and optional position (if XYZ position is omitted command sender's current position will be used).

### `/mp npc state <target> [state]`

Changes state of NPC entities found by `<target>` selector, with `[state]`. `[state]` can contain special notation in form of `<state_name>:[properties...]` which should allow to overwrite only specific properties of the NPC.

### `/mp npc set <target> <property> [data...]`

Changes specific `<property>` of NPC entities found by `<target>` selector, with `[data...]`. The format of `[data...]` is completely depends upon the given `<property>`.

## Faction commands

`/mp faction` command provides subcommands to work with [factions](./Factions):

### `/mp faction set <target> <id> <score>`

Sets the score of faction by `<id>` for player(s) found by `<target>` selector with `<score>`.

### `/mp faction add <target> <id> <score>`

Adds `<score>` to faction by `<id>` for player(s) found by `<target>` selector.

### `/mp faction clear <target> [id]`

Removes faction(s) score from player(s) found by `<target>` selector. If `[id]` is provided, then only that faction will be cleared, if `[id]` is omitted then all factions score will be cleaned.

## Data commands

`/mp data` is a utility command that allows to load and save player states for debugging purposes.

### `/mp data clear`

Resets all data of the entire playthrough. States will be fully reset, and every player's quests and inventory will be reset as well.

### `/mp data save <preset>`

Saves current state and current player's inventory and quests.

### `/mp data load <preset> [global] [player]`

Loads saved state and applies saved quests and inventory on given `[player]` (if `[player]` is omitted then the command will use the player that executed the command). `[global]` option allows to specify whether server states should be also updated from the saved state, by default it's enabled.