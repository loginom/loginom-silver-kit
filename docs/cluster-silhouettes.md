# Кластерные силуэты

[Назад к списку компонентов](../README.md)

## Назначение

Позволяет сформировать набор данных для графического построения кластерных силуэтов и проведения общей оценки качества кластеризации, выполненной внешним алгоритмом. В компоненте проводится:

* расчет индекса оценки силуэта для заданного числа точек (но не более 1000);
* расчет индекса силуэта для каждого кластера;
* расчет индекса силуэта кластеризации в целом;
* формирование метки качества кластеризации.

Внешний алгоритм кластеризации должен быть основан на каком-либо центроидном методе (т.е. оперировать понятием центра кластера), например, алгоритм k-средних.

## Входные порты

| Название         | Тип        |
|:-----------------|:-----------|
| Таблица объектов | Таблица    |
| Переменные       | Переменные |

### Структура таблицы "Таблица объектов"

| Метка          | Тип                                    | Описание                 |
|:---------------|:---------------------------------------|:-------------------------|
| Номер кластера | ![](./img/integer.svg) Целый           | Номер кластера, к которому относится объект     |
| Идентификатор  | ![](./img/string.svg) Строковый        | Идентификатор объекта    |
| Поле           | ![](./img/string.svg) Строковый        | Наименование поля, в котором содержится значение характеристики объекта кластера  |
| Значение       | ![](./img/realnumber.svg) Вещественный | Значение поля |

### Переменные в порте "Переменные"

| № | Метка                | Тип                                 | Значение   |
|:--|:---------------------|:------------------------------------|:-----------|
| 1 | Стандартизация данных| ![](./img/logical.svg) Логический |       true |

**Стандартизация данных** — флаг, при котором значения будут приведены к единому виду. По умолчанию **true**.

## Выходные порты

| Название               | Тип        |
|:-----------------------|:-----------|
| Кластерные силуэты     | Таблица    |
| Индексы силуэтов       | Таблица    |
| Качество кластеризации | Переменные |

### Структура таблицы "Кластерные силуэты"

| Метка                 | Тип                                    | Описание |
|:----------------------|:---------------------------------------|:---------|
| Номер строки          | ![](./img/integer.svg) Целый           | Порядковый номер строки  |
| Номер кластера        | ![](./img/integer.svg) Целый           | Номер кластера, к которому относится объект |
| Идентификатор         | ![](./img/string.svg) Строковый        | Идентификатор объекта   |
| Индекс оценки силуэта | ![](./img/realnumber.svg) Вещественный | Значение индекса оценки силуэта для объекта |

Таблица отсортирована по возрастанию номера кластера и убыванию индекса силуэта.

### Структура таблицы "Индексы силуэтов"

| Метка          | Тип                                    | Описание                  |
|:---------------|:---------------------------------------|:--------------------------|
| Номер кластера | ![](./img/integer.svg) Целый           | Уникальный номер кластера |
| Индекс силуэта | ![](./img/realnumber.svg) Вещественный | Индекс силуэта кластера   |

### Переменные в порте "Качество кластеризации"

| № | Метка                  | Тип                                    | Описание                               |
|:--|:-----------------------|:---------------------------------------|:---------------------------------------|
| 1 | Индекс силуэта         | ![](./img/realnumber.svg) Вещественный | Значение индекса силуэта кластеризации |
| 2 | Качество кластеризации | ![](./img/string.svg) Строковый        | Интерпретация значения индекса силуэта, см. **Алгоритмы** |

## Алгоритмы

Общее описание ([ссылка 1](https://en.wikipedia.org/wiki/Silhouette_%28clustering%29)) и подробный алгоритм с реализацией на языке Питон ([ссылка 2](http://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_silhouette_analysis.html#sphx-glr-download-auto-examples-cluster-plot-kmeans-silhouette-analysis-py)).

1. Индекс оценки силуэта **SilhouetteScore** расчитывается по формуле:

    ![SilhouetteScore =  \frac{BI - AI}{max(AI,BI)}](./img/1_cluster-silhouettes.svg), где:

    * ![AI](./img/2_cluster-silhouettes.svg) — Расстояние до центра кластера;
    * ![BI](./img/3_cluster-silhouettes.svg) — Расстояние до центра соседнего кластера.

2. Среднее значение индекса оценки силуэта **SilhouetteCoefficient** варьируется от -1 до 1.

3. Метка, отвечающая за качество кластеризации, формируется по правилу:

    * Качество кластеризации **Низкое**, если **SilhouetteCoefficient** < 0,2;
    * Качество кластеризации **Среднее**, если **SilhouetteCoefficient** в интервале [0,2; 0,5)
    * Качество кластеризации **Высокое**, если **SilhouetteCoefficient** > 0,5.

## Дополнительная литература

1. [Паклин, Н.Б., Орешков, В.И. Кластерные силуэты (2016)](https://elibrary.ru/item.asp?id=26506406)
