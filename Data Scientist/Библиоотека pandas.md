```python
import pandas as pd # загрузка pandas
```
### Создание датафрейма из матрицы
```python
data = [['Tomsk', 70],
        ['Omsk', 55]]
df = pd.DataFrame(data, columns=['city', 'code']) # columns — названия колонок
```
### Из списка словарей
```python
data = [{'city': 'Tomsk', 'code': 70},
        {'city': 'Omsk', 'code': 55}]
df = pd.DataFrame(data)
```
###  Из Series
```python
df = pd.DataFrame({'city': pd.Series(['Tomsk', 'Omsk']),
                  'code': pd.Series([70, 55])})
df['city'] # обращение к столбцу ‘city’
pd.Series(['Tomsk', 'Omsk'], name='city') # создание объекта типа Series
```

### Чтение файлов формата Excel
```python
df = pd.read_excel('partner_data.xlsx', sheet_name='partner_data1', header=0, index_col='id')
# header — строка с заголовками, index_col — колонка с индексами
```
### Запись файлов формата Excel
```python
dataframe.to_excel('data/...')
```
### Чтение файлов формата csv
```python
df = pd.read_csv('partner_data_semicolon.csv', sep=';', index_col='id')
# sep — разделитель
```
### Запись файлов формата csv
```python
dataframe.to_csv('data/...')
```
### Другие данные
```python
df.shape # размер датафрейма
df.columns # названия колонок
df.index # значения столбца index
df.head(10) # первые 10 строк
df.tail(10) # последние 10 строк
df.query("col == ...") # выбор элементов столбца по значению
```
### Выбор элементов по индексу
```python
df.iloc[0,0] # элемент на позиции [0,0]
df.iloc[0:3, 0] # элементы 0, 1, 2 нулевого столбца
df.iloc[:, 0] # полный срез столбца 0
df.iloc[0, :] # полный срез строки 0
```
### Выбор элементов по имени
```python
df.loc[1, 'age'] # строка с id 1, столбец age
df.loc[5:6, 'marital':'education'] # обе границы включаются в диапазон
df.loc[[5,10], ['marital','default']] # можно передавать списки
df['age'] # один столбец
df[['age', 'marital']] # несколько столбцов
```
### Чтение файлов json
```python
import json
json.load(file_obj) # принимает на вход объект файла
json.loads(file_obj.read()) # принимает на вход содержимое файла в виде строки
with open('partner_data_records.json', 'r') as j:
    contents = json.load(j)
contents[1] # элемент с индексом 1
contents[1]['balance'] # значение элемента 1 по ключу balance
df = pd.read_json('partner_data_records.json') # чтение json в датафрейм
df.set_index('id', inplace=True) # меняем колонку index на id, inplace сохраняет изменения в датафрейме
pd.read_json('partner_data_records_cp1251.json', encoding='cp1251') # чтение файла в кодировке Windows-1251 (cp1251)
```
### Подсчёт простых статистик
```python
df.describe() # выводит основные описательные статистики для числовых колонок
df['balance'].min() # выводит минимум по колонке balance
df.balance.min() # название колонки можно не помещать в кавычки и скобки
df.min() # минимум по всем колонкам
df.max(numeric_only=True) # максимум только для числовых столбцов
df.max(axis='columns') # максимум для каждой строки
df.max(axis=1) # можно вместо columns указать 1
df.mean() # среднее
df.median() # медиана
df.mode() # мода
df['balance'].values # все значения колонки balance
df['balance'].value_counts() # частоты каждого значения
df[['job', 'marital', 'education', 'housing', 'loan', 'default']].describe() # статистики по строковым столбцам
df['marital'].nunique() # количество уникальных значений в столбце
df['marital'].unique() # сами уникальные значения по столбцу
df['marital'].isna() # для всех строк проверяет, пропущено ли значение 
df[df['marital'].isna()] # строки датафрейма с None в marital
df[df['age'].isna()] # в числовом столбце значения NaN
df[df['age'].isna() & df['marital'].isna()] # выбор строк по несольким условиям
```
### Редактирование данных
```python
df.duplicated() # узнать есть ли дублирующие значения, возвращает булевую маску: 
# если для объекта условие выполняется, то для него вернется True, если нет Fals
df.info() # выводит информацию о датасете
df.drop(columns=['...']) # удаление столбца
df.drop_duplicates() # удаление дубликата
df.dropna #удаление записей (строк) или полей (столбцов), в которых встречаются пропуски
df.fillna('...') # замена пропущенного значения на то, что в скобках
df.replace('земеняемое значение', 'земеняющее значение') # метод для замены одного значения на другое
df.apply(lambda x: 'функция преобразующая x') # преобразование данных согласно функции, функцию можно наложить на определенные колонки передав соответствующую колонку 
(df.column)
df.insert('индекс', 'название столбца', 'данные') # вставить столбец в определенное место согласно 'индекса' (первый индекс равен - 0)
df.sort_values('колонка') # сортировка по колонке
df.select_dtypes('тип_данных').columns # выбор колонок по типу данных
```
### Группировка и агрегирование данных
```python
df.groupby('групирующий столбец').agg('агрегированный столбец', 'агрегирующая функция') 
# .groupby - функция группировки по заданному столбцу; 
# .agg - функция агрегирующая данные по столбцу и применяющая функци
```