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

Скачиваем необходимые инструменты:
```
sudo apt install graphviz
sudo apt install fim
```

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
Код программы:
```
include "alldifferent.mzn";%импорт ограничения на уникальность значений
array[1..6] of var 0..9: digits; %набор из 6 цифр

constraint sum(digits[1..3]) = sum(digits[4..6]);%условие равенства сумм

constraint all_different(digits);

solve minimize sum(digits[1..3]);
 output ["digits: \(digits)"];
```
![image](https://github.com/user-attachments/assets/1c3a1808-5f22-415a-a636-d336494714f5)

## Задание 5
Решить на MiniZinc задачу о зависимостях пакетов для рисунка, приведенного ниже.

![image](https://github.com/DefriDwamn/kisscm/blob/main/prac2/img/pubgrub.png)

```
% определение пакетов
  enum PACKAGES = {
      root, menu_1_0_0, menu_1_1_0, menu_1_2_0, menu_1_3_0, menu_1_4_0, menu_1_5_0,
      dropdown_2_0_0, dropdown_2_1_0, dropdown_2_2_0, dropdown_2_3_0, dropdown_1_8_0,
      icons_1_0_0, icons_2_0_0  };
  % переменные, показывающие, установлен пакет (1) или нет (0)
  array[PACKAGES] of var 0..1: installed;
  %  установка root
  constraint
      installed[root] == 1;
  % ограничения зависимостей
  constraint
  (installed[root] == 1) -> (installed[menu_1_0_0] == 1 /\ installed[menu_1_5_0] == 1 /\ installed[icons_1_0_0] == 1) /\
  (installed[menu_1_5_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
  (installed[menu_1_4_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
  (installed[menu_1_3_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
  (installed[menu_1_2_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
  (installed[menu_1_1_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
  (installed[menu_1_0_0] == 1) -> (installed[dropdown_1_8_0] == 1) /\
  (installed[dropdown_2_0_0] == 1) -> (installed[icons_2_0_0] == 1) /\
  (installed[dropdown_2_1_0] == 1) -> (installed[icons_2_0_0] == 1) /\
  (installed[dropdown_2_2_0] == 1) -> (installed[icons_2_0_0] == 1) /\
  (installed[dropdown_2_3_0] == 1) -> (installed[icons_2_0_0] == 1);
  % минимизация количества установленных пакетов
  solve minimize sum(installed);
  % вывод результата
  output [ "Installed packages: ", show(installed) ];
```
![image](https://github.com/user-attachments/assets/057ee0dc-f31e-48ff-bc77-ddab271741cd)

## Задание 6
Решить на MiniZinc задачу о зависимостях пакетов для следующих данных:
```
root 1.0.0 зависит от foo ^1.0.0 и target ^2.0.0.
foo 1.1.0 зависит от left ^1.0.0 и right ^1.0.0.
foo 1.0.0 не имеет зависимостей.
left 1.0.0 зависит от shared >=1.0.0.
right 1.0.0 зависит от shared <2.0.0.
shared 2.0.0 не имеет зависимостей.
shared 1.0.0 зависит от target ^1.0.0.
target 2.0.0 и 1.0.0 не имеют зависимостей.
```

```
  enum PACKAGES = {root,  menu_1_0_0, menu_1_1_0, menu_1_2_0, menu_1_3_0, menu_1_4_0, menu_1_5_0,
 dropdown_2_0_0, dropdown_2_1_0, dropdown_2_2_0, dropdown_2_3_0, dropdown_1_8_0, icons_1_0_0, icons_2_0_0 };
  
  array[PACKAGES] of var 0..1: installed;
  constraint installed[root] == 1;
  
  constraint (installed[root] == 1) -> (installed[menu_1_0_0] == 1 /\ installed[menu_1_5_0] == 1 /\ installed[icons_1_0_0] == 1) /\
      (installed[menu_1_5_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
      (installed[menu_1_4_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
      (installed[menu_1_3_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
      (installed[menu_1_2_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
      (installed[menu_1_1_0] == 1) -> (installed[dropdown_2_3_0] == 1 /\ installed[dropdown_2_0_0] == 1) /\
      (installed[menu_1_0_0] == 1) -> (installed[dropdown_1_8_0] == 1) /\ (installed[dropdown_2_0_0] == 1) -> (installed[icons_2_0_0] == 1) /\
      (installed[dropdown_2_1_0] == 1) -> (installed[icons_2_0_0] == 1) /\ (installed[dropdown_2_2_0] == 1) -> (installed[icons_2_0_0] == 1) /\
      (installed[dropdown_2_3_0] == 1) -> (installed[icons_2_0_0] == 1);

  solve minimize sum(installed); 
  output [ "Installed packages: ", show(installed) ];
```
![image](https://github.com/user-attachments/assets/5d0160a9-9e82-480d-b9dd-c63e11ec88e8)
