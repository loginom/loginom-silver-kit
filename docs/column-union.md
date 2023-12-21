# Объединение столбцов JS

[Назад к списку компонентов](../README.md)

## Назначение

Компонент для объединения столбцов в одну строку через произвольный разделитель.

## Входные порты

| Название                 | Тип        |
|:-------------------------|:-----------|
| Набор данных             | Таблица    |
| Входные переменные       | Переменные |

### Структура таблицы "Набор данных"

Структура таблицы не определена, в порте включена автосинхронизация.

### Переменные в порте "Входные переменные"

| № | Метка         | Тип                                  | Значение   |
|:--|:--------------|:-------------------------------------|:-----------|
| 1 | Разделитель   | ![](./img/string.svg) Строковый      | ,          |

## Выходные порты

| Название               | Тип        |
|:-----------------------|:-----------|
| Выходной набор данных  | Таблица    |

### Структура таблицы "Выходной набор данных"

| Метка           | Тип                                | Описание                 |
|:----------------|:-----------------------------------|:-------------------------|
| Выходная строка | ![](./img/string.svg) Строковый    | Строка после объединения |