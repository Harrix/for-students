# 11 IT класс

## Python

- Установка Python: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/install-python/install-python.md>
- Установка PyCharm: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/install-pycharm/install-pycharm.md>
- Сложение двух чисел в Python IDLE: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/add-2-num-python-idle/add-2-num-python-idle.md>
- Сложение двух чисел в PyCharm: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/add-2-num-pycharm/add-2-num-pycharm.md>
- Сложение двух чисел в Python на онлайн сервисах: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/add-2-num-python-web/add-2-num-python-web.md>
- Сложение двух чисел в Wing Python IDE: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/add-2-num-wing/add-2-num-wing.md>
- ложение двух чисел в Python через консоль и блокнот: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/add-2-num-python-console/add-2-num-python-console.md>
- Сложение двух чисел в Thonny на Python: <https://github.com/Harrix/harrix.dev-blog-2021/blob/main/add-2-num-thonny/add-2-num-thonny.md>

## Простые типы данных

```python
x = 5  # int - целые числа
second_var = 2.1  # float - вещественные числа
s = "Петя пришел домой."  # str - строки
b = True  # bool - логический тип данных (True, False)
n = None  # Отсутствие значения в переменной
```

## Преобразования типов данных

Тип данных выступает в роли функции, которая преобразует значение в указанный тип данных. Например, дан тип данных целых чисел `int`. Значит, функция `int()` будет превращать что-то в целые числа (например, `int(2.1)` вернет `2`).

```python
y = int(2.1)  # Значение: 2
y2 = int(True)  # Значение: 1
y3 = bool(1)  # Значение: True
```

```py
print(bool(10))  # Вывод: True
print(bool(-10))  # Вывод: True
print(bool("False"))  # Вывод: True
print(bool(""))  # Вывод: False
print(bool(None))  # Вывод: False
print(int(None))  # Вывод: TypeError: int() argument must be a string, a bytes-like object or a real number, not 'NoneType'
print(int("Петя"))  # Вывод: ValueError: invalid literal for int() with base 10: 'Петя'
print(int("78"))  # Вывод: 78
print(int(input()) + 1)  # Вывод: 78
```

`bool(0)`, `bool("")`, `bool(None)`, `bool(False)` дадут `False`. Остальные значения простых типов данных для `bool()` дадут `True`. На этом основана проверка пустой строки:

```python
if bool(s):
  ...
  # Строка s не пустая
if s:
  ...
  # Строка s не пустая
```

## Считывание чисел с консоли

```python
x = int(input()) # Считываем целое число
x2 = float(input()) # Считываем вещественное число
x3 = bool(input()) # Считываем булевское (логическое) значение: Так не делать!
x3 = bool(int(input())) # Считываем булевское значение: 0 или 1
```

Считать два числа, записанные в столбик:

```python
a = int(input())
b = int(input())
c = a + b
print(c)
```

Считать два числа в строчку:

```python
a, b = map(int, input().split())
c = a + b
print(c)
a, b = list(map(int, input().split())) # Иногда так лучше, например, с массивами
c = a + b
print(c)
```

## Строчка `a, b = map(int, input().split())`

```python
x1 = input()
print(x1)  # x1 равен '2 3'. Вывод: 2 3
x2 = x1.split()  # Вывод: ['2', '3']
print(x2)
x3 = map(int, x2)  # Вывод: <map object at 0x00000244D5557F10>
print(x3)
# x4 = list(x3)  # Вывод: [2, 3]
# print(x4)
x4, x5 = x3  # Аналогично (x4, x5) или [x4, x5]
print(x4, x5)  # Вывод: 2 3
```

Команда `input()` считывает строчку с консоли.

Команда `.split()` — это метод любой строки, которая разбивает строку на массив кусочков. По умолчанию, разбивает по пробелу.

- `"2 3".split()` выдаст массив из двух элементов `['2', '3']`.
- `"12++78".split()` выдаст массив из одного элемента `['12++78']`.
- `"12++78".split("++")` выдаст массив из двух элементов `['12', '78']`.
- `"12;78; 4".split(";")` выдаст массив из трех элементов `['12', '78', ' 4']` (обратите внимание на пробел).

Так как `input()` возвращает строчку, то `input().split()` разобьет по пробелу введенную строку в консоли. Ввели `2 3`, получим список (массив) `['2', '3']`.

Функция `map()` применяет указанную функцию (в нашем случае это `int()`) к каждому элементу массива (например, `['2', '3']`). Но на самом деле в момент выполнения кода `map(int, ['2', '3'])` никаких преобразований с массивом не делает. Это некий «договор», «обязательства» по преобразованию массива. Поэтому `print(map(int, ['2', '3']))` выведет не массив чисел, а что-то вида `<map object at 0x00000244D5557F10>`. Зачем это нужно? Например, позволяет значительно экономить оперативную память во многих задачах, но об этом позже.

Можно «заставить» `map()` выполнить свои обязательства. Например, через `list()`: `list(map(int, ['2', '3']))`. В этом случае мы получим именно массив чисел `[2, 3]`.

Или вот таким образом: `a, b = map(int, ['2', '3'])`. На самом деле здесь опять идет преобразование в список (точнее в кортеж), и эта строчка аналогична следующему коду:

```python
t = tuple(map(int, ['2', '3']))
a = t[0]
b = t[1]
```

Кстати, а что такое `tuple` (кортеж)? Это просто неизменяемый список, в котором нельзя изменять значения элементов.

Посмотрите разницу:

```python
# Список list
t = [2, 3]
print(t[0])  # Вывод: 2
print(t[1])  # Вывод: 3
t[0] = 6
print(t[0])  # Вывод: 6
```

```python
# Кортеж tuple
t = (2, 3)
print(t[0])  # Вывод: 2
print(t[1])  # Вывод: 3
t[0] = 6  # Ошибка: TypeError: 'tuple' object does not support item assignment
```

Более подробно о функции `map()` можно прочитать [тут](https://www.digitalocean.com/community/tutorials/how-to-use-the-python-map-function-ru).

## Найти минимальное число из двух

Способ 1:

```python
x1, x2 = 26, 11

if x1 < x2:
    min_x = x1
else:
    min_x = x2

print(min_x)  # Вывод: 11
```

Способ 2:

```python
x1, x2 = 26, 11

min_x = x1
if x2 < min_x:
    min_x = x2

print(min_x)  # Вывод: 11
```

Способ 3 (с помощью [тернарного оператора](https://ru.code-basics.com/languages/python/lessons/ternary-operator)):

```python
x1, x2 = 26, 11

min_x = x1 if x1 < x2 else x2

print(min_x)  # Вывод: 11
```

Способ 4 (встроенный метод):

```python
x1, x2 = 26, 11

min_x = min(x1, x2)

print(min_x)  # Вывод: 11
```

## Задача на поиск максимального числа из минимальных

**Условие.** Даны две строки, в каждой из которых записано произвольное число целых чисел, разделенных `;`. В каждой строке найти минимальное число, а затем найти из этих минимальных чисел максимальное.

Пример выходных данных:

```text
45;8;12
96;74;4256;85
```

Вывод для примера: `74`.

**Решение.**

```python
x1, x2 = map(int, input().split(";"))
y1, y2 = map(int, input().split(";"))
min_x = min(x1, x2)
min_y = min(y1, y2)
max_min = max(min_x, min_y)
print(max_min)
```

Или в одну строку:

```python
print(max(min(map(int, input().split(";"))), min(map(int, input().split(";")))))
```

## Задача ЕГЭ 15

Эту задачу почти всегда можно решить через перебор различных вариантов.

## Координатная плоскость

[Задача 17382](https://inf-ege.sdamgia.ru/problem?id=17382). Для какого **наименьшего** целого неотрицательного числа A выражение

$$
(5x + 3y ≠ 60) ∨ ((A > x) ∧ (A > y))
$$

тождественно истинно при любых целых неотрицательных x и y?

**Решение**. Решаем с использованием перебора и «лакмусовой бумажки»:

```python
def f(x, y, A):
    return ((5 * x + 3 * y != 60) or ((A > x) and (A > y)))

for A in range (0, 100):
    b = True
    for x in range (0, 100):
        for y in range(0, 100):
            ff = f(x, y, A)
            if ff == False:
                b = False
    if b == True:
        print(A)
        break
```

Более короткое решение:

```python
for A in range(0, 100):
    b = True
    for x in range(0, 100):
        for y in range(0, 100):
            b = b and (((5 * x + 3 * y) != 60) or ((A > x) and (A > y)))
    if b:
        print(A)
        break
```
