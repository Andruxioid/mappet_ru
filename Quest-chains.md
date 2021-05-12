Quest chains is a special data type that uses the node system (больше о системе нодов можно узнать на странице [нодов](https://github.com/Andruxioid/mappet_ru/blob/main/%D0%9D%D0%BE%D0%B4%D1%8B.md)) to represent quest progression. Quest chains are used within [dialogue system](./Dialogues) to provide [квесты](https://github.com/Andruxioid/mappet_ru/edit/main/%D0%9A%D0%B2%D0%B5%D1%81%D1%82%D1%8B.md) out of the dialogue.

Цепочками квестов можно управлять в [Главной панели Маппета](./Mappet-dashboard). The last panel in the left sidebar opens quest chain editor.

## Редактирование

Как только вы создадите или выберете цепочку квестов, вы увидите вот такой редактор:

![Редактор цепочек квестов](https://i.imgur.com/xaR0gwu.png)

Работает он ровно так же, как работает редактор диалогов или нодов в целом, однако он в своей системе имеет единственный тип нода - нод квеста.

### Нод квеста

Once you select a quest node beside the common **Title** field, there are also three fields:

* Поле **Квест** field determines the quest by the given ID that will be used to display in the dialogue
* **Квестодатель** это ID NPC, `[subject_id]` if the dialogue shown through `/mp dialogue open` [command](https://github.com/mchorse/mappet/wiki/Commands#mp-dialogue-open-target-id-subject_id), which will give quest, meaning you would be able to see the quest only if the NPC or the `[subject_id]` matches **Quest giver**
* **Quest receiver** same thing as **Quest giver** but for completing quests, i.e. which NPC/`[subject_id]` allows to hand in the completed quest

### Иерархия

Соединяя существующие ноды между собой, вы создаёте прогрессию по цепочке квестов. Ноды, у которых нету вводных соединений (соединений сверху), дают начало квестовым цепочкам, иными словами они являются первыми квестами в цепочках, в то время как все остальные квестовые цепочки после них открываются после того, как вы пройдёте квесты, от которых к дальнейшим цепочкам идут соединения.

Обратите внимание на следующую картинку:

![Пример цепочки квестов](https://i.imgur.com/FFei6X0.png)

В обоих случаях эти цепочки определённо будут работать, однако левая цепочка более читаема и интуитивна чем правая цепочка. 

* Левая цепочка читается как: завершите `da`, затем `test_nbt` а потом `test`, так вот это и работает.
* Правая цепочка читается как: завершите `easy`, затем `example`, а после этого `quest`, **ОДНАКО** вместо этого порядок на самом деле будет таковым: сначала `quest`, затем `example` и после него `easy`!

Так что, при привязке квестовых нодов, удостовертесь, что вы выбрали **первый нод снизу**, а только потом выбирайте верхний и привязывайте их только после того, как вы выбрали их именно в таком порядке.
