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
Решение реализовать в виде модели.  
Сделать оценку качества модели и описать ее преимущества.

### Описание решения

Факты, извлеченные из общения с заказчиком.

1. Набор признаков постоянно меняется: одни остаются, другие исчезают (например, связанные с разовыми акциями). Активно генерируются новые признаки.
2. Признаки создаются различными путями, в том числе генерацией производных признаков за разные временные промежутки.
3. С течением времени значения признаков могут изменяться и, как следствие, изменяется значимость этих признаков.
4. Регулярно осуществляется повторное обучение модели на новых данных.
5. Для заказчика приемлемо определенное значение метрики, определяющей качество модели. Основной метрикой выбрана ROC-AUC.

Принимая во внимание вышеописанные факты, было принято решение **сосредоточиться на сокращении количества признаков**, используемых для моделирования, при сохранениии приемлемого качества модели.
 
Премущества такого решения:
1. Закачик сможет регулярно обучать модель, затрачивая меньшее количество ресурсов.
2. Заказчик получит более стабильную серию моделей, легче поддающихся анализу.
3. Заказчик сможет скорректировать процесс генерации новых признаков.
4. Закачик сможет сосредоточиться на улучшении качества модели, благодаря существенному сокращению требуемых ресурсов для вычислений.
