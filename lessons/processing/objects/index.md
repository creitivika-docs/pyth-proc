## Теория

Зачем нужны объекты? Это способ упорядочить программный код, такой же, как функции, списки, словари. Он очень пригождается, когда количество строчек кода насчитывает уже сотни и тысячи. 

Что такое объекты? Это как Списки + свои команды//функции. То есть набор переменных + набор действий, которые собраны в одной штуковине. В любой игре персонаж, или враг, или орижие, и всё что угодно ещё — объекты. У объекта персонажа игрока есть встроенные переменные —  координаты, здоровье, уровень и т.д. Они называются свойствами или полями объекта. А встроенные действия, встроенные процедуры и функции объекта, называются методами.

Как создать объект? Нужно сначала создать его «чертёж». Наметить, что за переменные и методы в нём будут. Этот чертёж называется классом. Вот у меня есть снеговик

```python
size(600,400)

# Координаты и размер снеговика,
# точнее, его среднего шара
x = 300
y = 200
sSize = 50
push()
translate(x,y)
scale(sSize/10)
ellipse(0,0-5-3,6,6)
ellipse(0,0,10,10)
ellipse(0,0+5+8,16,16)
pop()
```

Сейчас я упакую его в класс. Сначала переменные.

```python
size(600,400)
# Координаты и размер снеговика,
# точнее, его среднего шара
class Snegovik:
    def __init__(self):
        self.x = 300
        self.y = 200
        self.sSize = 50
# А теперь по чертежу создадим объект
sn1 = Snegovik()

push()
translate(sn1.x,sn1.y)
scale(sn1.sSize/10)
ellipse(0,0-5-3,6,6)
ellipse(0,0,10,10)
ellipse(0,0+5+8,16,16)
pop()
```

__init__ — это важная встроенная функция, его конструктор, «собиратель». В ней мы пишем, какие поля(свойства, встроенные переменные) будут у будущего объекта, и она собирает их в единое целое.

sn1 = Snegovik()
Создаём переменную и вставляем в неё ссылку (указатель, ярлык) на новый объект класса. Snegovik — обратите внимание — с большой буквы. Названия классов пишутся с большой буквы, чтобы не путать их с просто функциями и т.д.

Snegovik() — это не только класс, но и функция. Она запускает __init__, который и создаёт класс.

Поля объекта пишутся через точку от его названия. Ведут себя как обычные переменные, можно в них записывать что угодно. sn1.x = 20 означает, что в sn1.x записывается число 20. А можно написать и sn1.x = sn1.x + 1 — увеличение на 1.

Self переводится как «себя». Так мы обозначаем, что x не просто x, а поле объекта. Так как по одному классу можно создать кучу объектов, у каждого разные названия. Если в  __init__ прописывается какой-то self.x и потом создаются объекты sn1,sn2, jeshoOdinSnegovik и т.д. — у всех них будет x. sn1.x, sn2.x, jeshoOdinSnegovik.x.

А теперь упакуем прорисовку снеговика в метод (встроенную функцию)

```python
size(600,400)

# Создадим класс — чертёж будущего объекта
class Snegovik:
    def __init__(self):
        self.x = 300
        self.y = 200
        self.sSize = 50
    def snDraw(self):
        push()
        translate(self.x,self.y)
        scale(self.sSize/10)
        ellipse(0,0-5-3,6,6)
        ellipse(0,0,10,10)
        ellipse(0,0+5+8,16,16)
        pop()      
          
# Создадим два объекта и у второго 
# Перед отрисовкой поменяем свойства
sn1 = Snegovik()
sn2 = Snegovik()
sn2.x = 500
sn2.sSize = 100

# А теперь оба нарисуем
sn1.snDraw()
sn2.snDraw()
```

У каждого нового снеговика одни и те же параметры. Приходится каждый отдельно переименовывать. А можно это как-то упростить, в одну строчку задать? Например, написать так:
sn1 = Snegovik(20,30,180)
sn2 = Snegovik(300,50,10)


И чтобы числа подставились куда надо? Да можно, можно. Только надо будет переделать класс, точнее, метод __init__ 

```python
size(600,400)
# Создадим класс — чертёж будущего объекта
class Snegovik:
    def __init__(self,sX,sY,ssSize):
        self.x = sX
        self.y = sY
        self.sSize = ssSize
    def snDraw(self):
        push()
        translate(self.x,self.y)
        scale(self.sSize/10)
        ellipse(0,0-5-3,6,6)
        ellipse(0,0,10,10)
        ellipse(0,0+5+8,16,16)
        pop()      
          
# Создадим два объекта с разными полями
sn1 = Snegovik(300,200,10)
sn2 = Snegovik(500,200,100)

# А теперь оба нарисуем
sn1.snDraw()
sn2.snDraw()
```

Теперь добавим в проект setup() и draw() и сделаем, чтобы снеговики двигались. С помощью метода move().

```python
# Создадим класс — чертёж будущего объекта
class Snegovik:
    def __init__(self,sX,sY,ssSize):
        self.x = sX
        self.y = sY
        self.sSize = ssSize
    def snDraw(self):
        push()
        translate(self.x,self.y)
        scale(self.sSize/10)
        ellipse(0,0-5-3,6,6)
        ellipse(0,0,10,10)
        ellipse(0,0+5+8,16,16)
        pop()
    def move(self, speedX,speedY):
        self.x = self.x + speedX
        self.y = self.y + speedY
        
# Создадим два объекта с разными полями
sn1 = Snegovik(300,200,10)
sn2 = Snegovik(500,200,100)

def setup():
    size(600,400)
    
def draw():
    background(100)    
    # А теперь оба нарисуем
    sn1.snDraw()
    sn2.snDraw()
    sn1.move(1,1)
    sn2.move(-2,3)

```



## Задания по теме «объекты и классы»

1. Создай персонажа через класс и объект с методами (встроенными функциями) прорисовки и движения на нажатие клавиш стрелок. Пример: голова кота, зайца. Можно использовать PImage для отрисовки
2. Создай класс «снежинка» с методом-конструктором и генерируй их по нажатию мыши на холст в месте, где нажимают. Можно вместо снежинки изобразить что-то другое. Если нажать мышью недалеко от центра существующей снежинки, она должна уничтожиться. Для вычисления расстояния между двумя точками используй формулу

3. Снег через объекты. Каждые несколько кадров генерируется объект-снежинка (белый кружок). Сделать переменную, которая задаёт переменчивый ветер, из-за которого снежинки не только падают вниз, но и движутся влево или вправо в зависимости от ветра. Для генерации снежинок раз в несколько кадров и смены ветра раз в несколько кадров используй переменную frameCount (номер текущего кадра) и остатоки от деления (if frameCount % 30 == 0:)
4. Пулемётная очередь. Создай класс объекта-пушки и класс пули. При нажатии на пробел создаётся объект-пуля и летит до края, после чего уничтожается. Так как пуля — объект, их может быть сколько угодно на холсте
5. Усложнённый проект из пункта 3 — по нижнему краю вправо-влево бегает пушка и стреляет. Пули летят вверх. Сверху падают бомбы/астероиды и т.д. При столкновении уничтожаются. Для проекта можно использовать два списка объектов — список пуль и список бомб.
6. Сделай свой проект через объекты.

## Команды и т.д.

**myPoint = {'x' : 10, 'y' : 23}** — создать словарь
**tasks= [“побрить руку”,”скукожиться”,”купить поп-сокет”]** — список дел(строк)
**len(tasks)** — количество элементов списка
**tasks.append(“выкинуть телек”)** — добавить элемент в конец списка
**del tasks[0]** — удалить начальный элемент списка
**del tasks[len(tasks)-1]** — удалить последний элемент списка
**text(tasks[1],200,300)** — вывести ВТОРОЙ элемент (индекс идёт с нуля) списка в 200 от левого края и 300 от правого края
**tasks[2] = “флексануть”** — теперь элемент с индексом 2 равен “флексануть”
**for element in tasks:** — для каждого элемента списка...
**for step in range(9):** — повторить 9 раз
**keyPressed** — нажата ли клавиша? Содержит True или False
**key** — переменная, содержит символ нажатой клавиши
**keyCode** —  если нажата ALT, CTRL, SHIFT или стрелка LEFT, RIGHT, UP, DOWN
при этом в key записывается CODED
**keyPressed() / keyReleased()** — когда клавиша нажата/когда клавиша отпущена
**textSize(20)** — размер текста
**textAlign(CENTER,CENTER)** — выравнивание текста по центру
**text(u”Привет”,200,300)** — вывести текст в 200 от левого края и 300 от правого края
**mouseClicked():** — функция, код в ней один раз срабатывает при нажатии мыши
**rotate(radians(30))** — повернуть систему координат на 30 градусов
**random(0,200)** — возвращает случайное число от 0 до 200. Не целое, но фигуры в Processing воспринимают нецелые параметры

Дополнительные задания/Задания для самостоятельной работы дома
1. Арканоид — посмотри в интернете, как работает эта игра. Кирпичики — объекты одного и того же класса. Вставляй их в список
2. Создай анимированный узор, который будет объектом. Его анимация должна быть методом (встроенной функцией)
3. Создай свой проект с использованием объектов