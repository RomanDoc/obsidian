изменяемый тип данных, набор пар ключ (key) : значение (value), где 
ключ - неизменяема структура данных (int, float, str, tupl), каждый ключ уникален
значение - любого типа структура данных, значение неуникально
#### Создание словаря
- `dict(x)`
- `{key: value}`
**пример:**
```python
a = {'one': 42, 'two': 3.14, 'ten': 'hello world'}
b = dict(one=42, two=3.14, ten='hello world')
c = dict([('one', 42), ('two', 3.14), ('ten', 'hello world')])
```
**Добавление нового значения в словарь**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e'}
x = 10
my_dict['ten'] = x
print(my_dict)
```
**результат:**  
```python
{'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
```
\# если такой ключ уже есть в словаре, то значение перезапишеться
Доступ к значению словаря через ключ (но не обратно)
`my_dict['ten']`
`my_dict.get('ten', 'defoult')` # defoult - выдаст это значение, если такого ключа нет
#### Методы

- `setdefault()` - метод возвращает значение по ключу, если нет такого ключа, то добавляет ключ в словарь и значение (None если значение не прописано).
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
spam = my_dict.setdefault('five')
print(f'{spam = }\t{my_dict = }')
eggs = my_dict.setdefault('six', 6)
print(f'{eggs = }\t{my_dict = }')
new_spam = my_dict.setdefault('two')
print(f'{new_spam = }\t{my_dict = }')
new_eggs = my_dict.setdefault('one', 1_000)
print(f'{new_eggs = }\t{my_dict = }')
```
**результат:**
```python
spam = None	my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10, 'five': None}
eggs = 6	my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10, 'five': None, six': 6}
new_spam = 3.14	my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10, 'five': None, 'six': 6}
new_eggs = 42	my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10, 'five': None, 'six': 6}
```

- `keys()` - метод возвращает итерируемый список ключей (`dict_keys`)
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
for key in my_dict.keys():
	print(key)
```
**результат:**
```python
one
two
three
ten
```

- `values()` - метод возвращает итерируемый список ключей (`dict_values`)
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
for value in my_dict.values():
	print(value)
```
**результат:**
```python
42
3.14
e
10
```

- `items()` - метод возвращает итерируемый список кортежей из двух значений, первое  - ключ и второе - значение
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
for key, value in my_dict.items():
	print(f'{key = }\t{value = }')
```
**результат:**
```python
key = 'one'	value = 42
key = 'two'	value = 3.14
key = 'three'	value = 'e'
key = 'ten'	value = 10
```

- `popitem()` - метод возвращает и удаляет из словаря последнею пару ключ: значение
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
spam = my_dict.popitem()
print(f'{spam = }\t{my_dict}')
eggs = my_dict.popitem()
print(f'{eggs = }\t{my_dict}')
```
**результат:**
```python
spam = ('ten', 10)	{'one': 42, 'two': 3.14, 'three': 'e'}
eggs = ('three', 'e')	{'one': 42, 'two': 3.14}
```

- `pop('key')` - метод возвращает значение словаря и удаляет из словаря пару ключ: значение по ключу
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
spam = my_dict.pop('ten')
print(f'{spam = }\t{my_dict}')
```
**результат:**
```python
spam = 10	{'one': 42, 'two': 3.14, 'three': 'e'}
```

-  `update()` - метод обновляет значения переданные ему по ключи и если нет в словаре такого ключа добавляет в конец этот ключ: значение
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
my_dict.update(dict(six=6))
print(my_dict)
my_dict.update(dict([('five', 5), ('two', 42)]))
print(my_dict)
```
**результат:**
```python
{'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10, 'six': 6}
{'one': 42, 'two': 42, 'three': 'e', 'ten': 10, 'six': 6, 'five': 5}
```
словари можно обновить или объединить с помощью знака "`|`"
**пример:**
```python
my_dict = {'one': 42, 'two': 3.14, 'three': 'e', 'ten': 10}
new_dict = my_dict | {'five': 5, 'two': 42} | dict(six=6)
print(new_dict)
```
**результат:**
```python
{'one': 42, 'two': 42, 'three': 'e', 'ten': 10, 'five': 5, 'six': 6}
```