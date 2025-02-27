---
title: Эффекты состояния
description: Узнайте, как создавать свои собственные эффекты состояния.
authors:
  - dicedpixels
  - YanisBft
  - FireBlast
  - Friendly-Banana
  - SattesKrokodil
authors-nogithub:
  - siglong
  - tao0lu
---

Эффекты состояния, также известные как просто эффекты, представляют собой состояние, которое может воздействовать на сущность. Они могут сказываться положительно, отрицательно или нейтрально на сущности. В обычном случае в игре эти эффекты применяются несколькими способами, такими как поедание еды, распитие зелий и так далее.

Можно использовать команду `/effect` для применения эффектов к сущности.

## Свои эффекты состояния {#custom-status-effects}

В этом руководстве мы добавим новый эффект под названием _Tater_, который даёт игроку одно очко опыта каждый игровой такт.

### Расширение `StatusEffect` {#extend-statuseffect}

Давайте создадим класс нашего эффекта, который будет наследовать основной класс всех эффектов — `StatusEffect`.

@[code lang=java transcludeWith=:::1](@/reference/1.21/src/main/java/com/example/docs/effect/TaterEffect.java)

### Регистрация своего эффекта {#registering-your-custom-effect}

Схожим с регистрацией блоков и предметов образом, мы используем `Registry.register`, чтобы зарегистрировать наш эффект в реестре `STATUS_EFFECT`. Это можно сделать в нашем инициализаторе.

@[code lang=java transcludeWith=:::1](@/reference/1.21/src/main/java/com/example/docs/effect/FabricDocsReferenceEffects.java)

### Текстура

Иконка эффекта состояния представляет собой PNG-файл размером 18×18 пикселей. Поместите свою иконку в папку:

```:no-line-numbers
resources/assets/fabric-docs-reference/textures/mob_effect/tater.png
```

<DownloadEntry visualURL="/assets/develop/tater-effect.png" downloadURL="/assets/develop/tater-effect-icon.png">Пример текстуры</DownloadEntry>

### Переводы {#translations}

Как и с любыми другими переводами, вы можете добавить запись формата `"effect.mod-id.<effect-identifier>": "Значение"` в языковой файл.

```json
{
  "effect.fabric-docs-reference.tater": "Tater"
}
```

### Тестирование

Используйте команду `/effect give @p fabric-docs-reference:tater`, чтобы дать игроку наш эффект Tater.
Используйте команду `/effect clear @p fabric-docs-reference:tater`, чтобы удалить эффект.

:::info
::: info
Чтобы узнать, как создать зелье, накладывающее этот эффект, ознакомьтесь с руководством по [зельям](../items/potions).
:::
