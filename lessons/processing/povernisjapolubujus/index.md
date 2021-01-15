---
title: Повороты и вращения
---
# Повороты и вращения

<iframe width="560" height="315" src="https://www.youtube.com/embed/8Tw08RyFMsY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Как повернуть фигуру относительно её центра? Перенести начало координат в центр фигуры с помощью translate():

```python
size(600,400)
translate(300,200)
rotate(radians(30))
ellipse(0,0,60,20)
```

## Задания по теме «Повороты и вращения»

### На статический поворот

Создать проект, сочетающий перенос координат (translate(x,y)) и поворот координат (rotate(TWO_PI/n) или rotate(radians(градусы))):
1. сердечко (два эллипса и повёрнутый квадрат)
2. Солнце/цветок
3. Медвежонок (лапки через rotate всё остальное без поворота)
4. Усложненный цветок (концентрический узор)
5. Своя идея


### На динамический поворот

1. Линия из центра. Вращаясь и меняя цвета, она оставляет отпечатки за собой
2. Круг в центре. С каждым кадром он отъезжает всё дальше вправо, при этом система координат поворачивается.
3. То же самое, только предыдущие варианты кружка не стираются, цвет и размер кружка случайные
4. Вращающийся концентрический узор
5. Сделать любую фигуру и попробовать повращать её
6. Своя идея проекта

## Команды и т.д.  
- angle = 0 — записать в переменную angle число 0
- rotate(radians(30)) — повернуть систему координат на 30 градусов
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
- background(255) — заливает весь холст одним цветом
- size(400,600) — задаёт размер холста 400 на 600

## В конце занятия ответь на эти вопросы, пожалуйста
<iframe src="https://docs.google.com/forms/d/e/1FAIpQLSctfl2kK9-gGcE97QpkNqQPHpaPUseV4SG5BfPy2DXrh6r4Ag/viewform?embedded=true" width="640" height="819" frameborder="0" marginheight="0" marginwidth="0">Загрузка…</iframe>

