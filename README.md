# TestZadanie
It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com) It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)
It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)
# Character Composition
## Создание внешности персонажа в редакторе
### Конфигурация Appearance
Для создания элементов внешности используется класс 
`Appearance`, который содержит список `SpriteSet2D`. 
`SpriteSet2D` представляет собой один элемент внешности и содержит
`SpriteSetData` который, в свою очередь, содержит 
 4 поля `Sprite2D`, для каждой из сторон света (south, north,
 west, east). 

Класс персонажа (например `Human`) содержит поле Appearance,
которое доступно для изменения в редакторе.

При добавлении нового `SpriteSet2D` в `Appearance`
необходимо заполнить `SpriteSetData` для этого набора спрайтов.
Есть 2 варианта: 

1. В `SpriteSetData` для каждой из сторон света настроить `Sprite2D`
(указать спрайт, его относительное положение, вращение, цвет и т.д.).

2. Если `SpriteSet2D` будет использоваться несколькими персонажами
(предметами и т.д.), то возможно создать данные для его 
`SpriteSetData` в виде ассета в проекте, чтобы использовать как 
общие данные. Для этого в меню `Assets/Create`
нужно выбрать `Appearance/Sprite Set Data`. Будет создан новый
`Sprite Set Data.asset` и в окне инспектора можно настроить
каждый Sprite2D.

При использовании второго способа, необходимо просто перетащить
созданный `Sprite Set Data.asset` в поле Value соответствующей
`SpriteSetData` и убедится, что галочка `Use Constant` снята.

Если используется второй способ, то необходимо отметить галочку 
`Use Constant`, развернуть `Constant Value`, и настраивать данные
в окне инспектора.

### Конфигурация Sprite2D
Для настройки Sprite2D применяется аналогичный подход. Sprite2D
содержит поля `Sprite` (сам спрайт) и `Properties` (параметры
 спрайта такие как относительное положение спрайта, вращение,
 цвет, слой, порядок сортировки).

Чтобы для каждого спрайта не изменять эти параметры каждый
 вручную, возможно создать `Sprite Properties.asset`
(`Assets/Create/Appearance/Sprite Property`), и добавить его в поле 
`SpriteProperties.Value`. Если эти настройки не будут общими для
нескольких Sprite2D, то можно отметить галочку `Use Constant` и 
использовать `Constant Value`.

## Создание внешности песонажа из кода
Для создания внешности Human из кода используется метод  
```c#
Human.CreateNew(SpriteSet2D body, SpriteSet2D hair)
```
который принимает `SpriteSet2D` соответственно для тела и для прически.

Т.е. при создании персонажа из кода алгоритм следующий:
```c#
Human human = Instantiate(humanPrefab).GetComponent<Human>();
human.CreateNew(body, hair);
```
