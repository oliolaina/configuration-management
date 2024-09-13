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
