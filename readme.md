# HUPERCYBEIIID

![https://duke-3d.deviantart.com/art/Cube-version-1-481881](https://gist.githubusercontent.com/codeleventh/a6b2ce4bf933c1689376ed0100111e85/raw/0b7a25a16dbc84a15a9202de7f0691bc3764a585/cube.png)

Визуализация кубов из фильма Куб.

Техзадание:  
✗ Генерация Куба (процент заполненности — входной параметр) и перемещение комнат в соответствии с фильмом  
✗ Трехмерная визуализация  
✗ Плавная анимация перемещений  
✗ Число одновременно перемещающихся кубов задается пользователем. При отсутствии значения (или значении, которое невозможно соблюсти) используется максимум возможного.  

Некоторые маленькие todo:  
✗ Возможность задавать высоту canvas перетаскиванием мышкой  
✓ Человеческий UI

Используется javascript и three.js.

- - - 

## Принцип работы Куба

Куб состоит из нагромождения кубических комнат. Максимальный размер Куба по каждой из граней — 26 комнат.
Комнаты могут не стоять друг на друге, но должны соприкасаться как минимум одной стороной в любой момент времени.

Каждая комната перемещается по замкнутому маршруту из трех позиций, заданных декартовыми координатами.  
Маршрут каждой комнаты задан исходной координатой и вектором смещений, которые закодированы в её Номер.

Номер — три группы по три цифры (например, `826 390 175`).  
Исходная координата комнаты получается сложением цифр в каждой группе: `(8+2+6, 3+9+0, 1+7+5) → (16, 12, 13)`.

Векторы смещений получаются путем вычитания цифр в каждой группе (второй из первой, третья из второй, первая из третьей):  
`826:      8-2=6     2-6=-4     6-8=-2`  
`390:     3-9=-6     9-0=9      0-3=-3`  
`175:     1-7=-6     7-5=2      5-1=4`  

Полученные векторы: `(6,-6,-6), (-4,9,2), (-2,-3,4)`.
Координата получаются путем сложения исходной координаты с векторами.

Итоговый маршрут для комнаты-примера:   
`(16, 12, 13) + (6,-6,-6) = (22, 6, 7)`  
`(22, 6, 7) + (-4, 9, 2) = (18, 15, 9)`  
`(18, 15, 9) + (-2, -3, 4) = (16, 12, 13)`

[Описание на Википедии](https://ru.wikipedia.org/wiki/%D0%9A%D1%83%D0%B1_%28%D1%84%D0%B8%D0%BB%D1%8C%D0%BC%29#%D0%9A%D1%83%D0%B1)

- - -



