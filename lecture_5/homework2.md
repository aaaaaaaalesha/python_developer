# # Домашка 2

Вам нужно реализовать модуль, который будет собирать информацию по заболевшим коронавирусом =)

## Объект Patient

Нужно хранить следующую информацию:

- имя
- фамилия
- дата рождения
- номер телефона
- тип документа, удостоверяющего личность (паспорт, загран либо водительские права)
- номер документа, удостоверяющего личность

Эта информация должна быть доступна соответственно из полей:

 - first_name
 - last_name
 - birth_date
 - phone
 - document_type
 - document_id

### Создание объекта

Объект больного должен поддерживать два способа создания:
- через конструктор: `Patient("Кондрат", "Коловрат", "1978-01-31", "+7-916-000-00-00", "паспорт", "4514 000000")`
- через метод create:  `Patient.create("Кондрат", "Коловрат", "1978-01-31", "+7-916-000-00-00", "паспорт", "4514 000000")`

Для каждого поля должна проводиться проверка правильности значения. При этом некоторые значения могут подаваться в разных вариантах, и их все нужно привести к единому виду. Например, телефон можно записать так: "89160000000", а можно "+7 (916) 000-00-00". Нужно учесть несколько вариантов.

Создание нового пользователя должно быть залогировано в файл. Если на вход поданы некорректные по формату данные, вызывается соответствующее исключение. Любое исключение должно быть залогировано в отдельный лог с ошибками.

### Изменение объекта

После создания объекта попытки изменить имя и фамилию должны вызывать ошибку (с логированием). Изменение остальных полей должно происходить с теми же проверками, что и в конструкторе. Логировать изменение поля также нужно (можно сделать общий лог для назначения поля извне и из `__init__`)

### Хранение объектов

Хранить полученные записи нужно в csv-файле. Можно работать с ним средствами питона, а можно через бибилотеку pandas. У объекта Patient должен быть метод `save`, при вызове которого он дозаписывается в файл. Сохранение объекта должно логироваться в файл с успешными логами. Ошибки - в лог с ошибками.

## Объект PatientCollection

Должен поддерживать следующий синтаксис:



```python
collection = PatientCollection(path_to_file)
for patient in collection:
    print(patient)
```

При этом patient должен быть объектом класса Patient.

Также должен быть метод `limit`, который будет возвращать итератор/генератор первых n записей:

```python
collection = PatientCollection(path_to_file)
for patient in collection.limit(8):
	print(patient)
```

При ручном изменении файла во время исполнения этого кода на следующей итерации нужно выдавать уже новые значения.

## Проверка задания

Я напилю скрипт, который проверяет основные моменты и выложу его на гитхаб. После того, как скрипт выдаст, что всё ок, можно делать пулл-реквест.
