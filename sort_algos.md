# Bubble sort
Time efficiency (best & worst): __O(n), O(n^2)__

Memory efficiency: __O(1)__

Is stable?: __yes__

***All code is written on Python***
```
def bubble_sort(array) -> list:
    if len(array) <= 1:
        return array
    else:
        for i in range(len(array) - 1): # key = a > b
            for j in range(len(array) - i - 1):
                if array[j] > array[j + 1]:
                    array[j + 1], array[j] = array[j], array[j + 1]
                else:
                    continue
    return array

print(bubble_sort([64, 88, 14565, 25232, 12415]))
```

# Merge sort
Time efficiency (best & worst): __O(n log n)__

Memory efficiency: O(1) (for list), O(n) (for array)

Is stable?: __nope__

```
def merge_sort(array) -> list:
    n = len(array)
    if n <= 1:
        return array
    mid = n // 2
    L = array[:mid]
    R = array[mid:]
    
    L = merge_sort(L)
    R = merge_sort(R)

    return merge(L, R)


def merge(Left, Right):
    merged = []
    while Left and Right:
        if Left[0] < Right[0]:
            merged.append(Left.pop(0))
        else:
            merged.append(Right.pop(0))
    merged.extend(Left or Right)
    return merged

print(merge_sort([123, 5351, 12315, 125162, 65, 351, 52, 67, 6767]))
```

# Selection sort

Time efficiency (best & worst): __O(n^2)__

Memory efficiency: __O(1)__

Is stable?: ***can be both stable 'n unstable***

```
def selection_sort(array):
    for i in range(len(array) - 1):
        for j in range(i + 1, len(array)):
            if array[i] > array[j]:
                array[i], array[j] = array[j], array[i]
    return array
```

# Insertion sort

Time efficiency (best & worst):  __always O(n^2)__

Memory efficiency: __O(n)__ ***for insertions***, __O(1)__ for auxiliary

Is stable?: __yeah__

```
def insertion_sort(array) -> list:
    n = len(array)
    for i in range(1, n):
        x = array[i]
        j = i - 1
        while j >= 0 and array[j] > x:
            array[j + 1] = array[j]
            j -= 1
        array[j + 1] = x
    return array


print(insertion_sort([12, 67, 88, 1337, 1987, 6767, 0, 5]))
```
