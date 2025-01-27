```Python
import numpy as np # загрузка numpy
```
#### Создание массива
Массив в `numpy` - это совокупность данных обладающая следующими свойствами:
- все элемента массива имеют один и тот-же тип;
- массив имеет одно имя для всех элементов;
- доступ к элементам массива осуществляется через индекс.
```Python
A = np.array([1, 2, 3])
A
# результат:
array([1, 2, 3])
```
обращение к элементам в массиве `numpy` происходит через индекс, нумерация индекса также как и в обычном списке начинается с нуля.
```Python
A[0]
# результат
1
# или
A[[1, 1, 1, 1, 1]]
# результат
array([2, 2, 2, 2, 2])
# или
A[[True, False, True]]
# результат
array([1, 3])
```
массив `numpy` также поддерживает срезы.
```Python
A[0:2]
# резулльтат
array([1, 2]) # послежний индекс невходит в выборку
# или
A[::-1]
# результат
array([3, 2, 1])
```
замена элементов в массиве `numpy`.
```Python
A[0] = 10
A
# результат
array([10, 2, 3])
```
процедур присвоение массиву имени также как и в обычном списке, это определения ссылки на ячейку памяти, со всеми вытекающими последствиями.
поиск элементов в массиве:
```Python
1 in A
# результат
True
# или
5 in A
# результат
False
```

функция `().any()` - проверяет есть хоть одно включение в массив
функция `().all()` - проверяет все значения
```Python
(A==1).any()
# результат
True
(A==1).all()
# результат
False
```
функция `np.unique()` - выводит массив уникальных значений
```Python
A = np.array([1, 1, 3, 1, 5, 3])
np.unique(A, return_counts=True) # return_counts=True выводит дополнительно кол-во этих уникальных значений
# результат
(array([1, 3, 5]), array([3, 2, 1]))
```
функция `np.zeros((кол-во))` - создает массив из нулей
функция `np.ones((кол-во))` - создает массив из единиц
```Python
A = np.zeros((10))
B = np.ones((5))
A
B
# результат
array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])
array([1., 1., 1., 1., 1.])
```
функция `np.eye(кол-во)` - создает единичную матрицу (массив)
функция `np.full((значение), кол-во повторений)` - создает массив из значений равный количеству повторений
```Python
A = np.full((10), 5)
A
# результат
array([5, 5, 5, 5, 5, 5, 5, 5, 5, 5])
```
функция `np.astype('тип данных')` - функция меняющая тип данных в массиве
функция `np.arange(начало, конец, шаг)` - функция создающая массив от значения начало до значения конец с определенным шагом (может создавать не только целочисленые но и с плавающей точкой). 
```Python
A = np.arange(5, 10, 2)
A
# результат
array([5, 7, 9])
```
функция `np.random....(знакчение)` - функция создающая массив на основе рандомных значений.
функция `массив.ravel()` - сглаживает массив (переделывает его в одномерный), создает представление массива
функция `массив.flatten()` - тоже сглаживает массив, но создает копию массива
функция `массив.size` - выводит общее кол-во элементов массива
функция `массив.shape` - выводит размерность массива, длину массива по каждой оси (nxm)
функция `массив.ndim` - выводит число осей (измерений) массива
функция `массив.reshape(размерность)` - изменяет размерность массива
функция `массив.T` - транспонирование массива (матрицы)
сложение двух массивов
```Python
A = np.array(1, 2, 3, 4)
B = np.array(5, 6, 7, 8)
A + B
# результат
array([6, 8, 10, 12])
```
также работает умножение, деление и вычетание. Главное условие, что бы массивы были одной размерности.
функция `np.hstack([массив_1, массив_2])` - соединяет массив по оси строки
функция `np.vstack([массив_1, массив_2])` - соединяет массив по оси столбца
```Python
A = np.array([1, 2], [3, 4])
B = np.array([5, 6], [7, 8])
A
B
# результат
array([[1, 2], 
	   [3, 4]])
array([[5, 6], 
	   [7, 8]])
np.hstack([A, B])
# результат
array([[1, 2, 5, 6], 
	   [3, 4, 7, 8]])
np.vstack([A, B])
# результат
array([[1, 2], 
	   [3, 4], 
	   [5, 6], 
	   [7, 8]])
```
функция `np.hsplit(массив, число_частей)` - разделяет массив на части по оси строки
функция `np.vsplit(массив, число_частей)` - разделяет массив на части по оси столбца
```Python
A = np.array([1, 2, 3, 4, 5, 6, 7, 8])
A
# результат
array([1, 2, 3, 4, 5, 6, 7, 8])
np.hsplit(A, 2)
# результат
[array([1, 2, 3, 4]), array([5, 6, 7, 8])]
A = np.array([[1, 2], [3, 4], [5,6], [7,8]])
A
# результат
array([[1, 2], 
	   [3, 4], 
	   [5, 6], 
	   [7, 8]])
np.vsplit(A, 2)
# результат
[array([[1, 2], 
		[3, 4]]), 
array([[5, 6], 
	   [7, 8]])]
```
необходимым условием, нужно чтобы массив был кратным тому числу на которое делим его
функции `массив.sum(), массив.mean(), массив.min(), массив.max()` - выводят соответственно сумму всех элементов массива, среднее всех элементов массива, минимальное и максимальное значение в массиве. При использование в скобках параметра `axis=0` - расчет идет по строкам и `axis=1` - расчет идет по столбцам массива.
(`массив.sum(axis=0)`)
функция `np.var(массив)` - вычисляет дисперсию массив
функция `np.std(массив)` - вычисляет  среднеквадратичную ошибку массива
функция `np.dot(массив_1, массив_2)` - скалярное произведение матриц, если применим обычное произведение `массив_1 * массив_2`, то получим поэлементное перемножение
```Python
A = np.array([1, 2], [1, 2])
B = np.array([2, 2], [2, 2])
A * B
# результат
array([[2, 4], 
	   [2, 4]])
```