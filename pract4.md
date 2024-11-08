# Практическое задание №4. Системы контроля версий

## Задача 1

На сайте https://onlywei.github.io/explain-git-with-d3 или http://git-school.github.io/visualizing-git/ с помощью команд эмулятора git получить следующее состояние проекта

![image](https://github.com/user-attachments/assets/be0ed5cf-4719-4975-be7f-f8346186b88d)


## Задача 2

Создать локальный git-репозиторий. Задать свои имя и почту (далее – coder1). Разместить файл prog.py с какими-нибудь данными. Прислать в текстовом виде диалог с git.

![image](https://github.com/user-attachments/assets/ce17cfd2-5ea0-425c-87f7-142b3d5fcb6d)


## Задача 3

Создать рядом с локальным репозиторием bare-репозиторий с именем server. Загрузить туда содержимое локального репозитория. Команда git remote -v должна выдать информацию о server! Синхронизировать coder1 с server.

![image](https://github.com/user-attachments/assets/a072cdd8-4bfc-4ce1-bc00-fdea3d55941e)


Клонировать репозиторий server в отдельной папке. Задать для работы с ним произвольные данные пользователя и почты (далее – coder2). Добавить файл readme.md с описанием программы. Обновить сервер.

![image](https://github.com/user-attachments/assets/9b409e2c-f84a-47a5-aca2-9441ffdc8865)


Coder1 получает актуальные данные с сервера. Добавляет в readme в раздел об авторах свою информацию и обновляет сервер.

![image](https://github.com/user-attachments/assets/de8aa1f6-7893-4b85-a346-80a38878a38b)


Coder2 добавляет в readme в раздел об авторах свою информацию и решает вопрос с конфликтами.

![image](https://github.com/user-attachments/assets/f47a5856-99d1-44c6-bc1f-86c39a2872d8)
![image](https://github.com/user-attachments/assets/bc9ebe86-eee6-4f7a-b5ca-83f539c0a59d)


Прислать список набранных команд и содержимое git log.

![image](https://github.com/user-attachments/assets/70a0688b-d473-4883-94b1-459798a2dee8)


## Задача 4

Написать программу на Питоне, которая выводит список содержимого всех объектов репозитория. Воспользоваться командой "git cat-file -p". Идеальное решение – не использовать иных сторонних команд и библиотек для работы с git.

## Код программы
```
from os import listdir, chdir
from subprocess import call


chdir('another_repo/')

if __name__ == '__main__':
    path = '.git/objects'
    lst = listdir(path)
    while len(lst) > 0:
        dr = lst.pop()
        if dr in {'info', 'pack'}:
            continue

        full_name = listdir(f'{path}/{dr}')[0]
        file = dr + full_name[:2]
        print('*' * 100)
        print(f'HASH: {dr + full_name}')
        print('*' * 100)
        call(['git', 'cat-file', '-p', file])
        print('\n' * 2)
```
![image](https://github.com/user-attachments/assets/191ffbff-d8ce-4209-9c0e-9c764e71a150)
![image](https://github.com/user-attachments/assets/5296f834-3365-44fb-812a-7b3c3e48fcc4)


