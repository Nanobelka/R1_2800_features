# Вероятность покупки клиентом оборудования в компании R1

### Цель

Компании **R1** необходимо предсказывать вероятность покупки клиентом нового оборудования.  
Заказчик уже имеет собственное решение (которое не раскрывает), но ищет пути его улучшения.

### Входные данные

Компания обладает базой клиентов, которым было предложено новое оборудование, а также указано, купил клиент оборудование или нет.
Датасет представляет собой выборку из базы клиентов, с которыми была попытка коммуникации.  
Таргет равен **1**, если после коммуникации с клиентом была продажа оборудования и **0**, если нет.

Обучающий набор содержит около **2.8 тысячи признаков и 700 тысяч наблюдений**.

### Задачи

Придумать решение на базе предоставленных данных, которое было бы интересно заказчику.  
Реализовать решение в виде модели.  
Сделать оценку качества модели и описать ее преимущества.

### Описание решения

#### Факты, извлеченные из общения с заказчиком

1. Набор признаков постоянно меняется: одни остаются, другие исчезают (например, связанные с разовыми акциями). Активно генерируются новые признаки.
2. Признаки создаются различными путями, в том числе генерацией производных признаков за разные временные промежутки.
3. С течением времени значения признаков могут изменяться и, как следствие, изменяется значимость этих признаков.
4. Регулярно осуществляется повторное обучение модели на новых данных.
5. Для заказчика приемлемо определенное значение метрики, определяющей качество модели. Основной метрикой выбрана ROC-AUC.

Принимая во внимание вышеописанные факты, было принято решение **сосредоточиться на сокращении количества признаков**, используемых для моделирования, при сохранениии приемлемого качества модели.
 
#### Премущества такого решения

1. Технологичность: процесс подготовки данных и обучения модели очень прост, не требует ручного труда и легко автоматизируем.
2. Закачик сможет регулярно обучать модель, затрачивая меньшее количество ресурсов.
3. Заказчик получит более стабильную серию моделей, легче поддающихся анализу.
4. Заказчик сможет скорректировать процесс генерации новых признаков.
5. Закачик сможет сосредоточиться на улучшении качества модели, благодаря существенному сокращению требуемых ресурсов для вычислений.

#### Основные этапы решения

1. Задание целевого количества признаков (первое значение задается эмпирически).
2. Удаление признаков с долей пропусков выше определенного порога.
3. Удаление признаков со слишком низкой и слишком высокой дисперсией.
4. Применение алгоритма RFECV в несколько итераций.
5. При необходимости, применение алгоритма RFE для сокращения количества признаков до целевого значения.
6. Контроль полученной метрики. При необходимости — изменение целевого количества признаков и повтор алгоритма с пункта 4.

Помимо задания целевого количества признаков, заказчик также может самостоятельно задать пороговые значения, используемые в пунктах 2 и 3 выше.

### Результат

Получена модель на базе 50 признаков.  
Метрика **ROC-AUC = 0.65**, что примерно на 1 п.п. ниже топового решения, построенного на нескольких сотнях признаков с применением большого количества ручного труда.

Бонус: ценой снижения метрики еще на 1 п.п. можно сократить количество используемых признаков до 15.


