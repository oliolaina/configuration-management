## Задание 1
Вывести служебную информацию о пакете matplotlib (Python). Разобрать основные элементы содержимого файла со служебной информацией из пакета.
Решение:

```

pip show matplotlib
```
![image](https://github.com/user-attachments/assets/bd5ca990-e575-418c-be55-a67a32ed235f)

Получить пакет без менеджера пакетов, прямо из репозитория можно командой

```

git clone https://github.com/matplotlib/matplotlib.git
```
![image](https://github.com/user-attachments/assets/3e6f7528-33b6-4d56-b266-f53d066ef1c9)

## Задание 2
Вывести служебную информацию о пакете express (JavaScript). Разобрать основные элементы содержимого файла со служебной информацией из пакета. 

![image](https://github.com/user-attachments/assets/d2ebed70-25a7-4b1b-b4d8-4493fc4fd164)

Получить пакет без менеджера пакетов, прямо из репозитория можно командой
```

git clone https://github.com/expressjs/express.git
```
![image](https://github.com/user-attachments/assets/12162537-b45a-40fa-a2df-2062f7ced0dc)


## Задание 3
Сформировать graphviz-код и получить изображения зависимостей matplotlib и express.
Для получения изображений зависимости mathplotlib нужно выполнить следующие команды:
```

echo 'digraph G { node [shape=box]; matplotlib [label="matplotlib"]; numpy [label="numpy"]; pillow [label="pillow"]; cycler [label="cycler"]; matplotlib -> numpy; matplotlib -> pillow; matplotlib -> cycler; }' > matplotlib.dot
dot -Tpng matplotlib.dot -o matplotlib.png
fim matplotlib.png
```
![image](https://github.com/user-attachments/assets/634004f4-8c8f-447c-97b6-972bf5be8e1a)

Аналогично с express:
```

echo 'digraph G { node [shape=box]; express [label="express"]; accepts [label="accepts"]; array_flatten [label="array-flatten"]; content_type [label="content-type"]; express -> accepts; express -> array_flatten; express -> content_type; }' > express.dot
dot -Tpng express.dot -o express.png
fim express.png
```
![image](https://github.com/user-attachments/assets/d110b553-50b4-4554-ba6d-317e9939219e)

## Задание 4
Изучить основы программирования в ограничениях. Установить MiniZinc, разобраться с основами его синтаксиса и работы в IDE.

Решить на MiniZinc задачу о счастливых билетах. Добавить ограничение на то, что все цифры билета должны быть различными (подсказка: используйте all_different). Найти минимальное решение для суммы 3 цифр.

