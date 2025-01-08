Модуль pickle в отличии от рассмотренных ранее форматов преобразует объект в набор байтов. Не занимается проверкой потока байтов перед распаковкой на безопасность. Не рекомендуется преобразовывать набор байт если вы не уверены в их безопасности.
**Допустимые типы данных для преобразования:**
- `None, True, False`
- `int, float, complex`
- `str, bytes, bytearrays`
- `tupl, list, set, dict` должны содержать объекты обрабатываемые pickl.
- Встроенные функции и функции написанные разработчиком, доступные в самом файле. Нельзя преобразовать lambda функции.
- Классы и экземпляры классов, доступные в самом файле.
#### Сериализация
`import pickl`
`pickl.dump('my_dict, file')`
сохраняет объекты в бинарном файле
**примеры:**
```python
import  pickle  
def func(a, b, c):  
    return a + b + c  
my_dict = {  
    "numbers": [42, 4.1415, 7+3j],  
    "functions": (func, sum, max),  
    "other": {True, False, 'hello world'},  
}  
with open('my_dict.pickle', 'wb') as f:  
    pickle.dump(my_dict, f)
```
`pickl_line = pikl.dumps(my_dict)`
сохраняет объект в строку байтов
**примеры:**
```python
import  pickle  
my_dict = {  
    "first_namt": "Джон",  
    "last_name": "Смит",  
    "hobbies": ["кузнечное дело", "пронраммирование", "путешествие"],  
    "age": 35,  
    "children": [  
        {  
            "first_name": "Алиса",  
            "age": 5  
        },  
        {  
            "first_name": "Маруся",  
            "age": 3  
        }  
    ]  
}  
print(my_dict)  
res = pickle.dumps(my_dict, protocol=pickle.DEFAULT_PROTOCOL)  
print(res)  
print(f'{pickle.DEFAULT_PROTOCOL = }')
```
**результат:**
```python
{'first_namt': 'Джон', 'last_name': 'Смит', 'hobbies': ['кузнечное дело', 'пронраммирование', 'путешествие'], 'age': 35, 'children': [{'first_name': 'Алиса', 'age': 5}, {'first_name': 'Маруся', 'age': 3}]}
b'\x80\x04\x95\xee\x00\x00\x00\x00\x00\x00\x00}\x94(\x8c\nfirst_namt\x94\x8c\x08\xd0\x94\xd0\xb6\xd0\xbe\xd0\xbd\x94\x8c\tlast_name\x94\x8c\x08\xd0\xa1\xd0\xbc\xd0\xb8\xd1\x82\x94\x8c\x07hobbies\x94]\x94(\x8c\x1b\xd0\xba\xd1\x83\xd0\xb7\xd0\xbd\xd0\xb5\xd1\x87\xd0\xbd\xd0\xbe\xd0\xb5 \xd0\xb4\xd0\xb5\xd0\xbb\xd0\xbe\x94\x8c \xd0\xbf\xd1\x80\xd0\xbe\xd0\xbd\xd1\x80\xd0\xb0\xd0\xbc\xd0\xbc\xd0\xb8\xd1\x80\xd0\xbe\xd0\xb2\xd0\xb0\xd0\xbd\xd0\xb8\xd0\xb5\x94\x8c\x16\xd0\xbf\xd1\x83\xd1\x82\xd0\xb5\xd1\x88\xd0\xb5\xd1\x81\xd1\x82\xd0\xb2\xd0\xb8\xd0\xb5\x94e\x8c\x03age\x94K#\x8c\x08children\x94]\x94(}\x94(\x8c\nfirst_name\x94\x8c\n\xd0\x90\xd0\xbb\xd0\xb8\xd1\x81\xd0\xb0\x94h\nK\x05u}\x94(h\x0e\x8c\x0c\xd0\x9c\xd0\xb0\xd1\x80\xd1\x83\xd1\x81\xd1\x8f\x94h\nK\x03ueu.'
pickle.DEFAULT_PROTOCOL = 4
```
#### Десериализация
`import pickle`
`new_dict = pickle.load(file)`
загрузка из бинарного файла и загрузка в объект
`new_dict = pickle.loads(data)`
получение объекта из бинарной строки