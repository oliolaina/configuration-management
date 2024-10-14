## Практическая работа №3
### Задание 1
Реализовать на Jsonnet приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.

```
{
  "groups": [
    "ИКБО-1-20",
    "ИКБО-2-20",
    "ИКБО-3-20",
    "ИКБО-4-20",
    "ИКБО-5-20",
    "ИКБО-6-20",
    "ИКБО-7-20",
    "ИКБО-8-20",
    "ИКБО-9-20",
    "ИКБО-10-20",
    "ИКБО-11-20",
    "ИКБО-12-20",
    "ИКБО-13-20",
    "ИКБО-14-20",
    "ИКБО-15-20",
    "ИКБО-16-20",
    "ИКБО-17-20",
    "ИКБО-18-20",
    "ИКБО-19-20",
    "ИКБО-20-20",
    "ИКБО-21-20",
    "ИКБО-22-20",
    "ИКБО-23-20",
    "ИКБО-24-20"
  ],
  "students": [
    {
      "age": 19,
      "group": "ИКБО-4-20",
      "name": "Иванов И.И."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Петров П.П."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Сидоров С.С."
    },
    <добавьте ваши данные в качестве четвертого студента>
  ],
  "subject": "Конфигурационное управление"
}
```
Код решения:
```
local x = 18;
local y = "ИКБО-%d-20";

local my_student(age=19, group=y % 10, name="Баймуратова А. А.") =
{
age: age,
group: group,
name: name
};

{
groups: [y % i for i in std.range(1, 24)],
students: [
my_student(19, y % 4, "Иванов И.И."),
my_student(x, y % 5, "Петров П.П."),
my_student(x, y % 5, "Сидоров С.С."),
my_student()
],
subject: "Конфигурационное управление"
}

```
![image](https://github.com/user-attachments/assets/15e4ef19-ca0c-41b1-9a35-2b877241c73b)


### Задание 2
Реализовать на Dhall приведенный выше пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.

Код решения:
```
{
 let generate = https://prelude.dhall-lang.org/List/generate
let index = https://prelude.dhall-lang.org/List/index

let makeGroup = \(i : Natural) -> "ИКБО-${Natural/show (i + 1)}-20"

let groups : List Text = generate 24 Text makeGroup

let get_group = \(i : Natural) -> index i Text groups

let makeStudent = 
  \(name : Text) -> 
  \(age : Natural) -> 
  \(groupIndex : Natural) ->
{ 
  name = name, 
  group_name = get_group groupIndex, 
  age = age 
}

let students = [ 
  makeStudent "Иванов И.И." 19 3, 
  makeStudent "Петров П.П." 18 4, 
  makeStudent "Сидоров С.С." 18 4,
  makeStudent "Баймуратова А.А." 18 9
]
      
let subject = "Конфигурационное управление"

in
{ 
  groups = groups, 
  students = students, 
  subject = subject
}
```
### Задание 3
Язык нулей и единиц.
```
10
100
11
101101
000
```

Код решения:
```
E = B | B E
B = 1 | 0
```
![image](https://github.com/user-attachments/assets/68824af0-4099-4422-99d4-e64e930b2f35)

### Задание 4
Язык правильно расставленных скобок двух видов.
```
(({((()))}))
{}
{()}
()
{}
```
Код решения:
```
E =  | ( E ) | { E } | E
```
![image](https://github.com/user-attachments/assets/702e9236-ee04-40b6-a24e-a4df3bdf1b2b)

### Задание 5
Язык выражений алгебры логики.
```
((~(y & x)) | (y) & ~x | ~x) & x
y & ~(y)
(~(y) & y & ~y)
~x
~((x) & y | (y) | (x)) & x | x | (y & ~y)
```
Код решения:
```
E = P | ~ E | E O E | ( E )
P = x | y
O = & | V
```
![image](https://github.com/user-attachments/assets/11398be6-9d49-4d48-824a-0de52ce2b6a5)
