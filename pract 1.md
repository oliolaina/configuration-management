# Задача 1
## Код программы:
```

cut -f1 -d: /etc/passwd | sort
```
![скрин](https://github.com/oliolaina/configuration-management/blob/main/prac%201%20task%201%20img.jpeg)
# Задача 2
## Код программы:
```

cat /etc/protocols | sort -k 2nr | head -n 5 | awk '{print $2, $1}'
```
![screen](https://github.com/oliolaina/configuration-management/blob/d1cc57ed653c201b4db1b882b07fccb7c03cdbcd/screenshots/pr1/task%202.jpg)
