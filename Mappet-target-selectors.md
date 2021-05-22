Mappet adds a couple of selectors to target selector system, which allow to target players and NPCs better.

# `mpid` selector

`mpid` selector allows to target NPC entities (`mappet:npc`) by their NPC ID. 

For example `@e[mpid=test]` will capture all the NPCs with their NPC ID `test`. You can also use `!` in front to target all NPCs whose NPC ID **isn't** what you want, so `@e[mpid=!test]` will target all NPCs whose NPC ID isn't `test`.

*more to come...*