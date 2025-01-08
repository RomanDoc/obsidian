упорядоченный динамический изменяемый массив хранящий адреса ячеек памяти с данными
#### Создание списка
- `list(x)`
- `[a, b, c, ...]`
**примеры:**
```python
a = list()
print(a)
b = list((3.14, True, 'Hello world'))
print(b)
c = []
print(c)
d = [3.14, True, 'Hello world']
print(d)
```
**результат:**
```python
[]
[3.14, True, 'Hello world']
[]
[3.14, True, 'Hello world']
```

Доступ к значению списка по индексу
`list[0]` - к первому значению с начала списка
`list[-1]` - к первому значению с конца списка
#### Методы

- `append()` - добавляет элемент в конец списка
**пример:**
```python
a = 42  
b = 'hello world'
c = [1, 3, 5, 7]  
my_list = [None]  
my_list.append(a)
print(my_list)
my_list.append(b)
print(my_list)
my_list.append(c)
print(my_list)
```
**результат:**
```python
[None, 42]
[None, 42, 'hello world']
[None, 42, 'hello world', [1, 3, 5, 7]]
```


- `extend()` - добавляет в конец списка по порядку значения из другой последовательности
**пример:**
```python
b = 'hello world'
c = [1, 3, 5, 7]
my_list = [None]
print(my_list)
my_list.extend(b)
print(my_list)
my_list.extend(c)
print(my_list)
my_list.extend(my_list)
print(my_list)
```
**результат:**
```python
[None]
[None, 'h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
[None, 'h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd', 1, 3, 5, 7]
[None, 'h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd', 1, 3, 5, 7, None, 'h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd', 1, 3, 5, 7]
```

- `pop('index')` - возвращает и удаляет элемент из списка, если не указан индекс, то последний элемент списка
**пример:**
```python
my_list = [2, 4, 6, 8, 10, 12]
spam = my_list.pop()
print(spam, my_list)
eggs = my_list.pop(1)
print(eggs, my_list)
```
**результат:**
```python
12 [2, 4, 6, 8, 10]
4 [2, 6, 8, 10]
```

- `count()` - возвращает и подсчитывает количество совпадений элементов в списке
**пример:**
```python
my_list = [2, 4, 6, 2,  8, 10, 12, 2, 4, 14, 2]
spam = my_list.count(2)
print(spam)
eggs = my_list.count(3)
print(eggs)
```
**результат:**
```python
4
0
```

- `index('значение', start, stop)` - возвращает индекс первого найденного значения в списке, start и stop задают диапазон поиска (можно и без них)
**пример:**
```python
my_list = [2, 4, 6, 2,  8, 10, 12, 2, 4, 14, 2]
spam = my_list.index(4)
print(spam)
eggs = my_list.index(4, spam + 1, 90)
print(eggs)
```
**результат:**
```python
1
8
```

- `insert('index', 'значение')` - добавляет значение в определенную позицию со сдвигом последующих значений
**пример:**
```python
my_list = [2, 4, 6, 8, 10, 12]
my_list.insert(2, 555)
print(my_list)
my_list.insert(-2, 13)
print(my_list)
```
**результат:**
```python
[2, 4, 555, 6, 8, 10, 12]
[2, 4, 555, 6, 8, 13, 10, 12]
```

- `remove()` - удаляет первый элемент в списке по значению
**пример:**
```python
my_list = [2, 4, 6, 8, 10, 12, 6]
my_list.remove(6)
print(my_list)
```
**результат:**
```python
[2, 4, 8, 10, 12, 6]
```

- `sort()` - сортирует список
**пример:**
```python
my_list = [4, 8, 2, 9, 1 , 7, 2]
my_list.sort()
print(my_list)
my_list.sort(reverse=True)
print(my_list)
```
**результат:**
```python
[1, 2, 2, 4, 7, 8, 9]
[9, 8, 7, 4, 2, 2, 1]
```

- `reverse()` - разворачивает список
**пример:**
```python
my_list = [4, 8, 2, 9, 1 , 7, 2]
my_list.reverse()
print(my_list)
```
**результат:**
```python
[2, 7, 1, 9, 2, 8, 4]
```

- `copy()` - создаёт поверхностную копию списка. Копирует непосредственно сами ячейки памяти, а не ссылки на них. Делает копию первого слоя данных.
**пример:**
```python
my_list = [2, 4, 6, 2, 8, 10, 12, 14, 16, 18]
new_list = my_list.copy()
print(my_list, new_list, sep='\n')
my_list[2] = 555
print(my_list, new_list, sep='\n')
```
**результат:**
```python
[2, 4, 6, 2, 8, 10, 12, 14, 16, 18]
[2, 4, 6, 2, 8, 10, 12, 14, 16, 18]
[2, 4, 555, 2, 8, 10, 12, 14, 16, 18]
[2, 4, 6, 2, 8, 10, 12, 14, 16, 18]
```

\# для полного копирования данных, всех слоев можно использовать функцию `deepcopy()` из метода `copy`
```python
import copy
new_list = copy.deepcopy(my_list)
```

#### Функции

- `sorted(`) - сортирует, но не изменяет список
**пример:**
```python
my_list = [4, 8, 2, 9, 1 , 7, 2]
sort_list = sorted(my_list)
print(my_list, sort_list, sep='\n')
rev_list = sorted(my_list, reverse=True)
print(my_list, rev_list, sep='\n')
```
**результат:**
```python
[4, 8, 2, 9, 1, 7, 2]
[1, 2, 2, 4, 7, 8, 9]
[4, 8, 2, 9, 1, 7, 2]
[9, 8, 7, 4, 2, 2, 1]
```

- `reversed()` - разворачивает список, но не изменяет список
**пример:**
```python
my_list = [4, 8, 2, 9, 1 , 7, 2]
res = reversed(my_list)
print(type(res), res)
rev_list = list(reversed(my_list))
print(rev_list)
for item in reversed(my_list):
    print(item)
```
**результат:**
```python
<class 'list_reverseiterator'> <list_reverseiterator object at 0x0000018EC5D2BBE0>
[2, 7, 1, 9, 2, 8, 4]
2
7
1
9
2
8
4
```

\# для разворота списка можно использовать `[::-1]`
```python
my_list = [4, 8, 2, 9, 1 , 7, 2]
new_list = my_list[::-1]
print(my_list, new_list, sep='\n')
```
**результат:**
```python
[4, 8, 2, 9, 1, 7, 2]
[2, 7, 1, 9, 2, 8, 4]
```

- `len()` - возвращает количество элементов в списке
**пример:**
```python
my_list = [2, 4, 6, 2, 8, 10, 12, 14, 16, 18]
matrix = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]
print(len(my_list))
print(len(matrix))
print(len(matrix[1]))
```
**результат:**
```python
10
3
4
```

#### Срезы
`list['start':'stop':'step']` - обрезает часть списка
**пример:**
```python
my_list = [2, 4, 6, 2, 8, 10, 12, 14, 16, 18]
print(my_list[2:7:2])
print(my_list[:7:2])
print(my_list[2::2])
print(my_list[2:7:])
print(my_list[8:3:-1])
print(my_list[3::])
print(my_list[:7:])
```
**результат:**
```python
[6, 8, 12]
[2, 6, 8, 12]
[6, 8, 12, 16]
[6, 2, 8, 10, 12]
[16, 14, 12, 10, 8]
[2, 8, 10, 12, 14, 16, 18]
[2, 4, 6, 2, 8, 10, 12]
```


