---
# ветвления 
## Номер 1.
```
print(max([float(input()) for i in range(3)]))
```
## Номер 2.
```
print("Чётное" if int(input()) % 2 == 0 else "Нечётное")
```
## Номер 3.
```
x, y = map(float, (input().split())) # ввод - 2 числа через пробел
r = float(input())

print('Лежит' if (((x ** 2) + (y ** 2)) ** 0.5) <= (r ** 2) ** 0.5 else 'Не лежит')
```
## Номер 4.
```
months = {"1": 31, "2": 28, "3": 31, "4": 30, "5": 31, "6": 30, "7": 31, "8": 31, "9": 30, "10": 31, "11": 30, "12": 31}
print(months.get(input()))
```
## Номер 5.
```
print(min([float(input()) for i in range(4)]))
```
## Номер 6.
```
v = float(input())
print('Упадёт на Землю' if v < 7.8 else 'Станет спутником земли' if 13.8 > v > 7.8 else 'Станет спутником Солнца' if 16.4 > v > 11.2 else 'Покинет Солнечную систему')
```
## Номер 7.
```
a = float(input())
r = float(input())

print('Круг может быть вписан в квадрат' if 2 * r == a else 'Квадрат может быть вписан в круг' if ((a ** 2) + (a ** 2)) ** 0.5 == r * 2 else "Фигуры никак не могут взаимодействовать")
```
## Номер 8 - wrong
```
b = ['Иванов', 'Петров', 'Сидоров']
ivanov, petrov, sidorov = [{'wins': 0, 'points1': int(input()), 'points2': int(input()), 'points3': int(input()), 'name': b[i]} for i in range(3)]


for i in range(1, 4):
    points = sorted([ivanov, petrov, sidorov], key=lambda x: x[f'points{i}'], reverse=True)
    for j in range(3):
        if points[0][f'points{i}'] > points[1][f'points{i}']:
            points[0]['wins'] += 1 


def win_res(a): # ввод - список словарей
    a[0]['points'], a[1]['points'], a[2]['points'] = sum([j for i, j in a[0].items() if i != 'wins' and i != 'name']), sum([j for i, j in a[1].items() if i != 'wins' and i != 'name']), sum([j for i, j in a[2].items() if i != 'wins' and i != 'name'])
    res = sorted(a, key=lambda x: x['wins'], reverse=True)
    if a[0]['wins'] > a[1]['wins']:
        print(f'{res[0]['name']} победил с {res[0]['points']} баллами')
    else:
        res = sorted(a, key=lambda x: x['points'], reverse=True)
        if res[0]['points'] > res[1]['points'] and res[0]['points'] > res[2]['points']:
            print(f'{res[0]['name']} победил в пересчёте с {res[0]['points']} баллами')
        else:
            print(f'Ничья: количество очков и побед одинаковое у участников')
    

win_res(points)
```
## Номер 9. 
```
Price, Money = float(input()), float(input())
print(f'Сдача {Money - Price}' if Money > Price else 'Спасибо' if Money == Price else f'Недостаточно {Price - Money}')
```
## Номер 10 - wrong
```
k = str(input())

if k == '1':
    suf = ''
elif k[0] == '1':
    suf = 'ов'
elif k[-1] in ['2', '3', '4']:
    suf = 'а'
else:
    suf = 'ов'
print(f'Мы нашли в лесу {k} гриб{suf}')
```
## Номер 11 wrong
```
k = str(input())

if k == '1':
    print('Мне 1 год')
elif k[-1] in ['2', '3', '4']:
    print(f'Мне {k} года')
elif k[-1] in ['5', '6', '7', '8', '9', '0']:
    print(f'Мне {k} лет')
elif k[-1] == '1':
    print(f'Мне {k} год')
```
## Номер 12 wrong
```
a, b, c, d = map(int, input().split())


if a <= b <= c <= d:
    print(sorted([a, b, c, d], reverse=True))


if a > b > c > d:
    pass
else:
    for i in [a, b, c, d]:
        print(i ** 2, end=' ')
```
## Номер 13.
```
a = int(input()) # 0 до 1000
count = 0
while a != 0:
    a //= 10
    count += 1
print(f'Количество разрядов: {count}')
```
## Номер 14.
```
matrix = [['0', '0', '0'], 
          ['0', '0', '0'], 
          ['0', '0', '0']]
for i in range(3):
    tic = int(input())
    matrix[(tic - 1) // 3][(tic - 1) % 3] = '1'


def tic_tac_toe(x) -> str:
    for i in x:
        if i.count('1') == 3:
            return 'Квадраты лежат на одной вертикали'
    count = 0
    for i in range(3):
        if x[i][i] == '1':
            count += 1
        if count == 3:
            return 'Квадраты лежат на одной диагонали'
    count = 0
    for i in range(2, -1, -1):
        if x[i][i] == '1':
            count += 1
        if count == 3:
            return 'Квадраты лежат на одной диагонали'
    
    for i in range(3):
        count = 0
        for j in range(3):
            if x[j][i] == '1':
                count += 1
            if count == 3:
                return 'Квадраты лежат на одной горизонтали'
    return 'Нет результата'


print(tic_tac_toe(matrix))
    
```
## Номер 15 wrong
```
a, b, c = (float(input()), float(input())), (float(input()), float(input())), (float(input()), float(input()))



def side(first, second) -> float:
    return (((second[0]) ** 2 - (first[0]) ** 2) + (second[1]) ** 2 - (first[1]) ** 2) ** 0.5


def main():
    global a, b, c
    if a[1] == b[1] == c[1] or a[0] == b[0] == c[0]:
        return 'Треугольник не существует: все точки лежат на 1 прямой'
    s1, s2, s3 = side(a, b), side(a, c), side(b, c)
    if s1 + s2 <= s3 or s2 + s3 <= s1 or s1 + s3 <= s2:
        return 'Треугольник не существует: длина 2 сторон мешьше 3 стороны'
    
    
    triangle = ''
    if s1 == s2 == s3:
        triangle = 'Равносторонний'
    elif s1 == s2 or s1 == s3 or s2 == s3:
        triangle = 'Равнобедренный'
    elif max([s1, s2, s3]) == (sum([s1 ** 2, s2 ** 2, s3 ** 2]) - max([s1 ** 2, s2 ** 2, s3 ** 2])) ** 0.5:
        triangle = 'Прямоугольный'
    else:
        triangle = 'Произвольный'


    perim = s1 + s2 + s3
    half_perim = perim / 2
    square = (half_perim * (half_perim - s1) * (half_perim - s2) * (half_perim - s3)) ** 0.5
    return f'{triangle}, периметр: {perim}, площадь: {square}'


print(main())
```
## Номер 16 wrong
```
point = (float(input()), float(input()))
diamond = (float(input()), float(input()))


if abs(point[0]) <= abs(diamond[0]):
    if abs(point[1]) <= abs(diamond[1]):
        print('Лежит')
        exit()
print('Не лежит')
```
## Номер 17.
```
brick = [float(input()), float(input()), float(input())]
hole = (float(input()), float(input()))


def main():
    global brick, hole
    for i in range(3):
        if brick[i] <= hole[0]:
            brick.pop(i)
            for j in range(2):
                if brick[j] <= hole[1]:
                    brick.pop(j)
                    return 'Пройдёт'
    return 'Не пройдет'


print(main())
```
## Номер 18.
```
from math import pi

a, b, c = map(float, input().split())
r = float(input())



def diagonal(x, y):
    return ((x ** 2) + (y ** 2)) ** 0.5

def main():
    global a, b, c, r
    d = sorted([a, b, c], reverse=True)
    if diagonal(d[-1], d[-2]) <= r * 2:
        return 'Пройдёт'
    return 'Не пройдёт'


print(main())
```
## Номер 19 wrong
```
i = int(input())

print('Високосный год' if i % 4 == 0 and i % 100 != 0 else 'Не високосный')
```
## Номер 20.
```
def calc(x, y, op):
    match op:
        case '+':
            return f'Результат: {x + y}'
        case '*':
            return f'Результат: {x * y}'
        case '/':
            return f'Результат: {x / y}'
        case '-':
            return f'Результат: {x - y}'
        case _:
            return 'Некорректная операция'
print(calc(float(input()), float(input()), input()))
```
## Номер 21.
```
x, y = map(float, input().split())

match x > 0:
    case True:
        print('1 четверть' if y > 0 else '4 четверть' if y != 0 else 'Точка на оси')
    case False:
        print('2 четверть' if y > 0 and x != 0 else '3 четверть' if x != 0 else 'Точка на оси')
```
## Номер 22.
```
d, m, y = map(int, input().split())

months = {"1": 31, "2": 28, "3": 31, "4": 30, "5": 31, "6": 30, "7": 31, "8": 31, "9": 30, "10": 31, "11": 30, "12": 31}

days = 0
for i in range(1, m):
    days += months.get(str(i))
else:
    days += d


print(days)
```
## Номер 23.
```
from math import ceil


x, y, z = input().split()


print(ceil(int(x + y + z) / 10) * 10)
```
## Номер 24 - work in progress
```
a1, a2 = (float(input()), float(input())), (float(input()), float(input()))
r1, r2 = float(input()), float(input())


def equation(x, y, radius, x1, y1) -> bool:
    cond = (((x1 - x) ** 2) + ((y1 - y)) ** 2) <= radius
    return cond


def dist(start, end) -> float:
    return ((end[1] - start[1]) ** 2) + (((end[0]) - start[0]) ** 2)


def intersec(start, end, r1, r2):
    for i in range()

def main():
    global a1, a2
    if dist(a1, a2) == 0:
        return 'Круги входят друг в друга'
    elif dist(a1, a2) <
```
## Номер 25 - wrong
```
print(True if len(set(str(input()))) == 3 else False)
```
## Номер 26
```
field1 = str(input()).lower() # ввод - шахматное поле вида "a1"
field2 = str(input()).lower() # ввод - шахматное поле вида "a1"

x1, y1 = field1[0], int(field1[1])
x2, y2 = field2[0], int(field2[1])


notation = {'a': 0, 'b': 1, 'c': 2, 'd': 3, 'e': 4, 'f': 5, 'g': 6, 'h': 7}

x1, x2 = notation.get(x1), notation.get(x2)

def black(x, y):
    if x % 2 == 0 and y % 2 == 1 or y % 2 == 0:
        return True
    return False

if black(x1, y1) == black(x2, y2):
    print('Поля являются одного цвета')
else:
    print('Поля не являются одного цвета')
```
## Номер 27
```
field1, field2 = str(input()), str(input())

notation = {'a': 0, 'b': 1, 'c': 2, 'd': 3, 'e': 4, 'f': 5, 'g': 6, 'h': 7}

x1, x2 = notation.get(field1[0]), notation.get(field2[0])
y1, y2 = int(field1[1]), int(field2[1])

def diag(x1, y1, x2, y2) -> bool:
    for i in range(1, 9):
        if x1 == x2 - i:
            if y1 == y2 - i:
                return True
            elif y1 == y2 + i:
                return True
        elif x1 == x2 + i:
            if y1 == y2 + i:
                return True
            elif y1 == y2 - i:
                return True
    return False

def main():
    global x1, y1, x2, y2
    if diag(x1, y1, x2, y2) or (x1 == x2 or y1 == y2):
        print(f'Ферзь на {field2} Угрожает полю {field1}')
    else:
        print(f'Ферзь на поле {field2} не угрожает полю {field1}')
main()
```
## Номер 28 - wrong
```
A, B, C = (float(input()), float(input())), (float(input()), float(input())), (float(input()), float(input()))

def lenght(x1, x2, x3):
    return (min(x1, x2, x3), max(x1, x2, x3))


def height(y1, y2, y3):
    return (min(y1, y2, y3), max(y1, y2, y3))


def main():
    global A, B, C
    if min(lenght(A[0], B[0], C[0])) <= 0.0 <= max(lenght(A[0], B[0], C[0])) and  min(height(A[1], B[1], C[1])) <= 0.0 <= max(height(A[1], B[1], C[1])):
        return 'Лежит'
    return 'Не лежит'

print(main())
```
## Номер 29 - wrong
```
x, y = float(input()), float(input())

print(f'{x} метров - ближайшее растояние до бортика бассейна' if x <= y else f'{y} метров - ближайшее растояние до бортика бассейна')
```
## Номер 30 - wrong
```
x = float(input())
if x <= 0:
    raise ValueError('Число лет должно быть больше нуля')

years = 0
if x - 2 >= 0:
    years += 21
    x -= 2
else:
    years = (x / 2) * 21
    x = 0


while x != 0:
    years += 7
    x -= 1

print(years)
```
## Номер 31
```
a, b, c = float(input()), float(input()), float(input())


D = (b ** 2) - (4 * a * c)

if D > 0:
    x1, x2 = ((-b) + (D ** 0.5)) / (2 * a), ((-b) - (D ** 0.5)) / (2 * a)
    print(x1, x2) 
elif D == 0:
    x1 = (-b) / (2 * a)
    print(x1)
else:
    print('Корней нет')
```
