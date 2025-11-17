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
## Номер 8.   
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
