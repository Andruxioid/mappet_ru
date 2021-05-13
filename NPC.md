NPC это сущности Маппета, которых можно использовать для целого вороха вещей. Они могут быть торговцами, собеседниками, квестодателями, спутниками, врагами, боссами и так далее. С ними вы можете делать так много всего, что все использования перечислить попросту невозможно. NPC используют морфы, что даёт вам право выбрать его внешний вид полностью на свое усмотрение.

NPC можно призвать командой `/mp npc summon`, или посредством инструмента NPC и редактировать используя команду `/mp npc` [команды](https://github.com/Andruxioid/mappet_ru/blob/main/%D0%9A%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D1%8B.md#mp-npc-state-target-state) или исполльзуя инструмент NPC.

NPC можно управлять в [главной панели Маппета](https://github.com/Andruxioid/mappet_ru/blob/main/%D0%93%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F%20%D0%BF%D0%B0%D0%BD%D0%B5%D0%BB%D1%8C%20%D0%9C%D0%B0%D0%BF%D0%BF%D0%B5%D1%82%D0%B0.md). Третья панель в левом боком меню открывает редактор NPC.

## Редактирование

Как только вы создадите или выберете NPC, перед вами появится вот такой редактор:

![Редактор NPC](https://i.imgur.com/mDe1NQt.png)

В нём вы можете редактировать параметры свойств и состояний каждого отдельного NPC. В этом редакторе вы, по сути, создаёте и настраиваете чертежи NPC дабы добиться от них желаемого поведения. 

### Главные опции

Here is the description of what main options on the top do:

* **Дистанция нахождения пути** позволяет установить максимальное расстояние пути по которому NPC будет идти в поисках своих целей в мире. Чем выше значение, тем больше нагрузка на центральный процессор.
* **Уникальный** (**ещё не используется**) в будущем позволит сделать NPC уникальным, означая то, что сервер возьмёт на себя обязанности по спавну этого NPC дабы с ним не возникло никаких инцидентов.

### Состояния

Слева от редактора главных опций вы увидите список состояний. Они позволят вам настроить разные варианты одного и того же NPC и потом сменять их используя [команду](https://github.com/Andruxioid/mappet_ru/blob/main/%D0%9A%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D1%8B.md#mp-npc-state-target-state) `/mp npc state`. Точно так же, как и в других модулях Маппета, вы можете кликнуть правой кнопкой мыши по списку чтобы добавить или удалить состояния, а также кликнуть по списку чтобы отредактировать состояние.

`default` это название состояния по умолчанию, использующееся всякий раз когда не указывается конкретное состояние NPC.

### Настройки

Здесь находится описание всех доступных настроек:

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

#### Поведение

* **Смотрит на игрока** будет ли NPC смотреть на игрока
* **Осматривается** будет ли NPC осматриваться по сторонам в состоянии бездействия
* **Бродит** будет ли NPC бродить туда-сюда по локации
* Напоследок у нас есть большой перечень [триггеров](https://github.com/Andruxioid/mappet_ru/blob/main/%D0%A2%D1%80%D0%B8%D0%B3%D0%B3%D0%B5%D1%80.md) на все случаи жизни:
    * **При инициализации NPC** which gets triggered upon NPCs summoning via a command or NPC tool.
    * **При взаимодействии с NPC** which gets triggered upon player right clicking the NPC.
    * **При получении урона NPC** which gets triggered when an NPC gets hurt.
    * **При смерти NPC** which gets triggered when an NPC dies.
    * **На тике NPC** which gets triggered every tick when an NPC exists.
    * **На цели NPC** (**ещё не используется**) which will be used when an NPC targets an entity


## Инструмент NPC

Инструмент NPC это предмет, находящийся в таблице Маппета режима творчества, который позволяет игроку упростить процесс редактирования и настройки NPC.

![Инструмент NPC](https://i.imgur.com/QV5SpBn.png)

Сперва, возьмите себе новый инструмент таблицы режима творчества; вам будет необходимо настроить инструмент кликнув правой кнопкой мыши с зажатой кнопкой Шифт. Появится вот такое меню: 

![Экран инструмента NPC](https://i.imgur.com/3h7vdTe.png)

Здесь вы можете выбрать ID NPC, которого вы хотите заспавнить и желаемое состояние этого самого NPC. Как только вы выберете ID и состояние, вы можете закрыть меню и кликнуть правой кнопкой мыши по земле, чтобы заспавнить NPC с выбранным ID и состоянием. 

Кроме того, вы также можете редактировать отдельные свойства NPC ровно так же, как в редакторе NPC:

![Редактор отдельных NPC](https://i.imgur.com/Ubct0va.png)

Как только вы закроете меню, NPC обновится.
