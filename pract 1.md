# Задача 1
## Код программы:
```

cut -f1 -d: /etc/passwd | sort
```
![скрин](https://github.com/oliolaina/configuration-management/blob/d9763c90d001a266e4caf3b9e608a3ccd8ac0e67/screenshots/pr1/task1.jpeg)
# Задача 2
## Код программы:
```

cat /etc/protocols | sort -k 2nr | head -n 5 | awk '{print $2, $1}'
```
![screen](https://github.com/oliolaina/configuration-management/blob/d1cc57ed653c201b4db1b882b07fccb7c03cdbcd/screenshots/pr1/task%202.jpg)

# Задача 3
## Код программы:

```

#!/bin/bash
string=$1
size=${#string}
echo -n "+"
for ((i=-2;i<size;i++))
do
echo -n "-"
done
echo "+"
echo "| $string |"
echo -n "+"
for ((i=-2;i<size;i++))
do
echo -n "-"
done
echo "+"
```
![image](https://github.com/user-attachments/assets/729d6916-e4ec-4240-9ab3-41d411efcd2c)


# Задача 4
## Код программы:
```

grep -o '\b[a-zA-Z_][a-zA-Z0-9_]*\b' main.cpp | sort | uniq
```
![image](https://github.com/user-attachments/assets/34e0a586-1463-4982-999b-d494fb96b87d)


# Задача 5
## Код программы:
```

#!/bin/bash
chmod +x "$1"
sudo cp "$1" /usr/local/bin/

```
![image](https://github.com/user-attachments/assets/04e4c384-95b9-4cf5-8ea9-5b4834b72baa)


# Задача 6
## Код программы:
```

#!/bin/bash

for file in "$@"; do
  # Проверка на наличие допустимого расширения
  if [[ "$file" =~ \.(c|js|py)$ ]]; then
    first_line=$(head -n 1 "$file")

    # Проверка на комментарий в первой строке для разных типов файлов
    if [[ "$file" =~ \.c$ && "$first_line" =~ ^// ]] || \
       [[ "$file" =~ \.js$ && "$first_line" =~ ^// ]] || \
       [[ "$file" =~ \.py$ && "$first_line" =~ ^# ]]; then
      echo "$file has a comment in the first line."
    else
      echo "$file does not have a comment in the first line."
    fi
  fi
done
```
![image](https://github.com/user-attachments/assets/40d44376-4187-4c8f-a300-63cf87653219)


# Задача 7
## Код программы:
```


```


# Задача 8
## Код программы:
```


```


# Задача 9
## Код программы:
```


```


# Задача 10
## Код программы:
```


```

