---
title: Переменные и анимация
published: true
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/wK4_h23O0NU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Немного теории текстом

Мы уже знаем, как подставлять в параметры команд случайные числа и таким образом менять рисунок с каждым кадром. Так у нас получились интересные анимации. Но что, если мы хотим сделать так, чтобы точка рисовалась не в случайном месте, а двигалась по прямой линии? Или эллипс равномерно увеличивался с каждым кадром, или уменьшался? Для этого нам пригодятся переменные.

Переменная — это ячейка для хранения каких-то данных в памяти компьютера. Вы можете представить себе её как ящичек. Только положить в этот ящичек можно только что-то одно — число или слово, например. Если решите положить что-то другое, старое выбросится — значение переменной перезапишется.

Как использовать переменную? Просто написать её имя — оно так же, как имя команды или функции, состоит из латинских символов и цифр. Только скобок нет — так переменные от команд и функций Python отличает. И имя переменной вы придумываете сами.

Вот я создаю переменую и записываю в неё число 5:
x = 5

А теперь я поменяю число в переменной:
x = 10

Что такое «=»? Функция? Команда? Это оператор. Только отличающийся. Этот оператор, оператор присваивания, не подставляет вместо себя и операндов значение. Он работает как команда, пишется с новой строки. Он записывает то, что справа от него (правый операнд) в переменную, которая указана слева. Если переменной не существует к этому моменту, она будет создана. Оператор «=» называется оператором присваивания. Можно читать поначалу „x = 10“ как «икс становится равно десяти». Опытные программисты прочитают иначе: «икс присваивается значение десять». Что в общем-то значит примерно то же самое. 

Вот посмотрите, сейчас я сделаю, чтобы эллипс двигался влево, увеличивая число в его первом параметре на 1 (не забудьте про background в начале кадра, чтобы стереть предыдущий кадр).

```python
x = 0
def setup():
	size(600,400)
def draw():
	global x
	background(100)
	ellipse(x, 200, 20,20)
	x = x + 1
```

## Задания теме «Анимация и переменные»

1. Сделай проект, в котором круг будет двигаться из левого верхнего угла в правый нижний. Попробуй стирать предыдущий кадр. А потом не стирать и назначить кругу случайные цвет и размер
2. Сделай проект, в котором четыре эллипса расходятся из центра в углы холста. Сначала стирая предыдущий кадр, потом — не стирая, назначая случайные цвет и размер. 
3. Круг размером больше холста уменьшается на 10 за кадр. На каждом кадре цвет меняется на случайный. Сделал? А теперь попробуй поменять скорость уменьшения, убрать заливку, сделать случайной цвет обводки или наоборот, убрать её.
4. Из центра по косой линии движется точка. Теперь сделай, чтобы это была не точка, а конец линии, начало которой всегда в центре. Не стирай предыдущие кадры. Используй случайный цвет.
5. Чёрный треугольник в центре постепенно светлеет с каждым кадром. Сделал? Сделай, чтобы одна из его вершин двигалась в определённом направлении. Две вершины. Три.
6. Поставь в setup команду colorMode(HSB). В центр помести эллипс. Сделай первый параметр команды fill переменным, увеличивай каждый кадр на 1. Сделал? Попробуй теперь сделать переменным только второй параметр fill. Только третий.

## Команды и т.д.
- x = 0 — записать в переменную 
- translate(200,300) — прибавляет ко всем X после себя число 200 и ко всем Y после себя число 300. ellipse(0,0,30,30) после этой команды на самом деле нарисуется в точке 0+200,0+300
- random(0,200) — возвращает случайное число от 0 до 200. Не целое, но фигуры в Processing воспринимают нецелые параметры
- frameRate(5) — задаёт частоту кадров 5 кадров в секунду.
- line(x1,y1,x2,y2) — линия по двум точкам x1,y1 и x2,y2
- triangle(x1,y1,x2,y2,x3,y3) — треугольник, в параметрах три точки (вершины)
- ellipse(30,20,80,60) — рисует эллипс с центром в точке 30,20 и размером 80 на 60
- rect(30,20,80,60) — прямоугольник с углом в точке 30,20 и размером 80 на 60
- rectMode(CENTER) — режим отрисовки прямоугольника «от центра»
- ellipseMode(CORNER) — меняет отрисовку эллипса на «от левого верхнего угла»
- strokeWeight(5) — меняет толщину штриха (точек, линий, обводки) на 5
- noStroke() — убирает обводку
- stroke(22,21,255) — меняет цвет штриха на новый в формате RGB
- fill(100) — меняет цвет заливки на оттенок серого. Можно вписать три числа (RGB)
- noFill() — убирает заливку, прозрачная заливка
- background(255) — заливает весь холст одним цветом
- size(400,600) — задаёт размер холста 400 на 600

## Задачи на IDLE

Время познакомиться циклами. Начнём с while. Он работает как if, только код в нём выполняется не один раз, а пока условие в круглых скобках выполняется. Создай файл с таким кодом и запусти:

num = input(“Введите 5: ”)
while(num != “5”):
	num = input(“Это не 5! Введите 5: ”)
print(“Вот теперь 5!”)

Пока пользователь не введёт «5», программа снова и снова будет требовать ввести это число. «!=» — оператор «не равно». Цикл закончится, когда текст в num будет равен «5», тогда сработает команда в последней сторчке. А теперь упражнения:


0. С консоли вводится пароль. Пока пароль не совпадает с заданным, программа сообщает, что он неверный и снова требует ввести пароль.
1. С консоли вводятся логин и пароль. Сначала вводится логин, и вводится пока не совпадёт с имеющимся логином.  После того, как логин введён успешно — начинается ввод пароля, пока не будет всё  успешно. Когда и пароль верен — появляется сообщение об успешном входе
2. То же самое, только логин и пароль вводятся в одном цикле, если что-то неправильно — выводится сообщение «Логин или пароль не верен»
3. То же самое, только чётко указывается, пароль или логин неверный. Если неверны оба, пишется только про логин.
4. «Угадай число». Пользователь вводит число одно за другим, пока не отгадает, какое число загадал компьютер.
5. Скидка. С консоли вводится потраченная на покупку сумма. Каждые 10 рублей дают бонус, который прибавляется к бонусам за прошлые покупки. Когда бонусов накопится 1000, всплывает сообщение «Бонусы накоплены, время тратить!». Цикл останавливается.
6. Консольный калькулятор. Пишет «введите операцию». Операция +, -, *, / . После этого, в зависимости от операции, пишет «введите первое слагаемое» и получает из консоли, или «делимое» и получает его и т.д. Потом второе число — второе слагаемое или делитель и т.д. В консоль выводится результат. И такое продолжается, пока калькулятор не получит вместо операции слово «exit»