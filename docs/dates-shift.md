# Сдвиг дат

[Назад к списку компонентов](../README.md)

## Назначение

Компонент для сдвига даты на одну или несколько единиц измерения времени.

## Входные порты

| Название   | Тип        |
|:-----------|:-----------|
| Даты       | Таблица    |
| Переменные | Переменные |

### Структура таблицы "Даты"

| Метка        | Тип                                | Описание                     |
|:-------------|:-----------------------------------|:-----------------------------|
| Список дат   | ![](./img/datetime.svg) Дата/Время | Временной ряд                |

### Переменные в порте "Переменные"

| № | Метка             | Тип                                | Значение              |
|--:|:------------------|:-----------------------------------|:----------------------|
| 1 | Направление сдвига| ![](./img/string.svg) Строковый    | +                     |
| 2 | Годы              | ![](./img/integer.svg) Целый       | 0                     |
| 3 | Месяцы            | ![](./img/integer.svg) Целый       | 0                     |
| 4 | Дни               | ![](./img/integer.svg) Целый       | 0                     |
| 5 | Часы              | ![](./img/integer.svg) Целый       | 0                     |
| 6 | Минуты            | ![](./img/integer.svg) Целый       | 0                     |
| 7 | Секунды           | ![](./img/integer.svg) Целый       | 0                     |

**Направление сдвига** — переменная, принимающая два значения:

 * **+** (плюс) — прибавляет указанные единицы измерения времени к исходной дате (по умолчанию);
 * **-** (минус) — вычитает указанные единицы измерения времени к исходной дате;

 ## Выходные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Выходной набор данных   | Таблица    |

### Структура таблицы "Выходной набор данных"

| Метка        | Тип                                | Описание                                     |
|:-------------|:-----------------------------------|:---------------------------------------------|
| Список дат   | ![](./img/datetime.svg) Дата/Время | Преобразованный временной ряд                |
