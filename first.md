---
# ветвления   
## Номер 8.   
```
b = ['Иванов', 'Петров', 'Сидоров']
ivanov, petrov, sidorov = [{'wins': 0, 'points1': int(input()), 'points2': int(input()), 'points3': int(input()), 'name': b[i]} for i in range(3)]


for i in range(1, 4):
    points = sorted([ivanov, petrov, sidorov], key=lambda x: x[f'points{i}'], reverse=True)


for i in range(1, 4):
    a, b, c = ivanov[f'points{i}'], petrov[f'points{i}'], sidorov[f'points{i}']
    if len(set([a, b, c])) == 3: # проверка на уникальные значения и однозначную победу
        if max(a, b, c) == a:
            ivanov['wins'] += 1
        elif max(a, b, c) == b:
            petrov['wins'] += 1
        else:
            sidorov['wins'] += 1
    else:
        if points[0][f'points{i}'] == points[2][f'points{i}']: # согласно свойству неравенств, если a == с, b == c, то a == b == c
            pass
        elif points[0][f'points{i}'] == points[1][f'points{i}']: # согласно свойству неравенств, если a == b, b > c, то a > c
            pass
        elif points[0][f'points{i}'] > points[1][f'points{i}']: # список неуникален, значения повторяются и значения отличаются на некоторое значение -> 1-ое значение наибольшее
            points[0]['wins'] += 1


def win_res(a): # ввод - список словарей
    a[0]['points'], a[1]['points'], a[2]['points'] = sum([j for i, j in a[0].items() if i != 'wins' and i != 'name']), sum([j for i, j in a[1].items() if i != 'wins' and i != 'name']), sum([j for i, j in a[2].items() if i != 'wins' and i != 'name'])
    res = sorted(a, key=lambda x: x['wins'], reverse=True)
    if a[0]['wins'] > a[1]['wins']:
        print(f'{res[0]['name']} победил с {res[0]['points']} баллами')
    else:
        res = sorted(a, key=lambda x: x['points'], reverse=True)
        if len(set([res[0]['points'], res[1]['points'], res[2]['points']])) == 3:
            print(f'{res[0]['name']} победил в пересчёте с {res[0]['points']} баллами')

        elif len(set([res[0]['points'], res[1]['points'], res[2]['points']])) == 2:
            if res[0]['points'] == res[1]['points']:
                print('Ничья: одинаковое количество баллов и побед у 2 ведущих участников')
            elif res[0]['points'] > res[1]['points']:
                print(f'{res[0]['name']} победил в пересчёте с {res[0]['points']} баллами')
        else:
            print(f'Ничья: одинаковое количество баллов и побед у всех участников')
    

win_res(points)
```
