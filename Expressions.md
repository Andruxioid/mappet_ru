Expression is a special line of code (or rather mathematical expression) that allows to check for specific conditions. Expressions support full power of McLib's math parser, which supports basic arithmetic operations (`+`, `-`, `*`, `/`), math functions (`abs()`, `sin()`, `cos()`, `sqrt()`, etc.) and many other things. For more information check out [this page](https://github.com/mchorse/aperture/wiki/Math-Expressions).

Beside that, expressions support special features that allow to connect it with other Mappet's features. Here is a full list of them:

### Quest functions

|Name and arguments|Return value|
| ---------------- | ---------- |
|`quest_present(id, target)`|Returns boolean whether one of the players by `target` selector has a quest by `id` in progress|
|`quest_completed(id, target)`|Returns boolean whether one of the player by `target` selector has completed a quest by `id`. Alternatively `~` can be used, for `target`, to check whether quest was completed globally.|
|`quest_present_or_completed(id)`|Returns boolean whether a quest by `id` was completed or one of the current players has it, this useful if you want to check whether the quest by `id` wasn't taken before.|

### Faction functions

|Name and arguments|Return value|
| ---------------- | ---------- |
|`faction_friendly(id, target)`|Returns boolean whether faction score of the faction by `id` of player by `target` selector makes it friendly.|
|`faction_neutral(id, target)`|Returns boolean whether faction score of the faction by `id` of player by `target` selector makes it neutral.|
|`faction_hostile(id, target)`|Returns boolean whether faction score of the faction by `id` of player by `target` selector makes it hostile.|
|`faction_has(id, target)`|Returns boolean whether player by `target` selector has faction score by `id`.|
|`faction_score(id, target)`|Returns faction score of faction by `id` of a single player by `target` selector.|

### State functions

|Name and arguments|Return value|
| ---------------- | ---------- |
|`state(id[, target])`|Returns value of state by `id`. If `target` is omitted, then it would use global state, or current subject's states. If `target` is specified, then it will try to find by a target selector a player with that state, or `~` for global state.|

### Player inventory functions

|Name and arguments|Return value|
| ---------------- | ---------- |
|`inv_has(item_id[, target, all])`|Returns boolean whether player(s) by `target` selector has an item by `item_id` in the inventory (not in held or equipped slots). `all` is a boolean that signifies whether (value `1`) all players should be checked, or only one (value `0`) player should have at least.|
|`inv_holds(item_id[, target, all])`|Returns boolean whether player(s) by `target` selector holds an item by `item_id` in main or off hands.|
|`inv_armor(item_id[, target, all])`|Returns boolean whether player(s) by `target` selector equipped an item by `item_id` in any of the armor slots.|

### Player functions

|Name and arguments|Return value|
| ---------------- | ---------- |
|`player_xp(target)`|Returns `target` player's current total XP.|
|`player_xp_level(target)`"|Returns `target` player's current XP level.|
|`player_hp(target)`|Returns `target` player's current HP.|
|`player_hunger(target)`|Returns `target` player's hunger.|
|`player_armor(target)`|Returns `target` player's armor.|
|`player_is_alive(target)`|Returns whether `target` player(s).|

### Dialogue functions

|Name and arguments|Return value|
| ---------------- | ---------- |
|`dialogue_read(id, target)`|Returns whether given `target` has read dialogue by `id`.|

### World functions

|Name and arguments|Return value|
| ---------------- | ---------- |
|`world_time()`|Returns world time (i.e. the one that actually is day/night), whether `1000` is `day` and `13000` is `night`.|
|`world_total_time()`|Returns total world time since the beginning of world's initialization.|
|`world_is_night()`|Returns boolean whether it's night time (12000 - 24000).|
|`world_is_day()`|Returns boolean whether it's day time (0 - 12000).|

**Note**: boolean is either `1` (true) or `0` (false).