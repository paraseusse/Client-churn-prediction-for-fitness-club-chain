# Прогнозирование вероятности оттока пользователей для фитнес-центров

### Используемые библиотеки: `python`,`pandas`,`seaborn`, `sklearn`,`sklearn.model_selection`, `StandardScaler`, `LogisticRegression`, `RandomForestClassifier`, `KMeans`, `sklearn.metrics`, `sklearn.cluster`

## Задача
- Прогноз вероятности оттока (на уровне следующего месяца) для каждого клиента
- Формирование типичных портретов пользователей
- Анализ признаков, наиболее сильно влияющих на отток
- Выводы и рекомендации по повышению качества работы с клиентами:
    - выделить целевые группы клиентов
    - предложить меры по снижению оттока
    - определить другие особенности взаимодействия с клиентами
    
![Матрица корреляций](<https://raw.githubusercontent.com/paraseusse/Client-churn-prediction-for-fitness-club/main/%D0%92%D0%B8%D0%B7%D1%83%D0%B0%D0%BB%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F/Denfrogram.jpeg?token=AMTEIGEQSUNXMPO6AKMPBCC7X2LIM>)

## Содержание
- Описание проекта
- Задачи проекта
- Исследовательский анализ данных
- Модель прогнозирования оттока пользователей
- Кластеризация пользователей
- [Выводы](#conclu)
- [Рекомендации](#recomend)

# Выводы<a id="conclu"></a>

### Мы обучили две модели — логистической регрессей и случайным лесом
- Доля правильных прогнозов и полнота незначительно выше у модели логистической регрессии
- Площадь под кривой ошибок — AUC-ROC=0.9
- Самые весомые признаки
    - средняя частота посещений в неделю за предыдущий месяц
    - количество месяцев с момента первого посещения
    - средняя частота посещений в неделю за все время
    - возраст
    - длительность текущего действующего абонемента

## Наблюдения по всем данным 

Доля оттока — 27%
- Разделение по полу относительно равное 51% и 49%
- Более 80% проживают или работают в районе фитнес-центра
- Чуть менее половины — 48% — сотрудники компании-партнёра клуба
- 30% пришли по акции «приведи друга»
- У 90% клиентов есть контактный телефон
- 40% клиентов хотя бы один раз посещали групповые занятия

- Средняя длительность текущего действующего абонемента 4.6 месяцев, медиальное значение — 1 месяц
- Средний возраст клиента — 29 лет
- Среднее средней суммарнаой выручки от других услуг фитнес-центра — 146.9 условных единиц
- Средний срок до окончания договора — 4.3 месяцев
- Среднее время с момента первого обращения — 3.7 месяцев
- Средняя частота посещений за все время — 1.87 раз в неделю
- Средняя частота посещений за предыдущий месяц — 1.76 раз в неделю


## Наблюдения в разбивке клиент-отток
- Распределение по полу — средние не различаются
- Живущие или работающие рядом с клубом клиенты немногим реже попадают в отток — 0.87 у текущих, 0.76 у ушедших
- Сотрудники компаний-партнеров реже попадают в отток — 0.53 у текущих, 0.35 у ушедших
- Пришедшие по акции «Приведи друга» в 2 раза реже попадают в отток — 0.35 у текущих, 0.18 у ушедших
- Наличие мобильного номера клиента — средние не различаются
- У текущих клиентов средняя длительность договора составляет 5.7, в оттоке срок договора составляет 1 месяц
- Среди ушедших меньше тех, кто посещал групповые занятия — 0.46 у текущих, 0.26 у ушедших

- Средний возраст в группах различается, в оттоке — 26.9, в оставшихся — 29.9
- Среднее средней суммарной выручки от других услуг фитнес-центра — 158.4 у текущих, 115.08 у ушедших
- Средний срок до окончания договора — 5.28 месяца у текущих, 1.66 месяца у ушедших
- Среднее время с момента первого обращения в фитнес-центр (в месяцах) — 4.71 месяца у текущих, 0.99 месяца у ушедших
- Средняя частота посещений за все время — 2 раза в неделю у текущих, 1.47 месяца у ушедших
- Средняя частота посещений за предыдущий месяц аналогично — 2 раза в неделю у текущих, 1.04 месяца у ушедших

## Кластеризация клиентов 

### Самый низкий процент оттока — 3%. Кластер 1. 
#### Выделяются длительностью абонемента и групповыми занятиями
- Живут или работатют недалеко от центра
- Более третьи пришли по партнерской программе
- Почти 60% пришли по акции «Приведи друга»
- Абонементы на 12 месяцев
- Чуть более половины из них посещают групповые занятия
- Частота посещений — 1,98 раза в неделю

#### По признакам, которые отметил алгоритм в порядке убывания веса 
1. Средняя частота посещений от 1.33 до 2.64 за предыдущий месяц
2. Количество месяцев с момента первого посещения от 2 до 6 месяцев
3. Средняя частота посещений в неделю за все время от 1.31 до 2.65 раз в неделю
4. Возраст 28-32
5. Длительность текущего действующего абонемента от 6 месяцев
 
### Низкий процент оттока —7%. Кластер 3. 
#### Выделяются частотой посещения, короткими абонементами
- Живут или работают недалеко от центра
- Абонементы на 3, 6 месяцев
- Менее половины из них посещают групповые занятия
- Частота посещений — 2,85 раз в неделю

#### По признакам, которые отметил алгоритм в порядке убывания веса 
1. Средняя частота посещений от 2.3 до 3.24 за предыдущий месяц
2. Количество месяцев с момента первого посещения от 2 до 7 месяцев
3. Средняя частота посещений в неделю за все время от 2.33 до 3.21 раз в неделю
4. Возраст 28-32
5. Длительность текущего действующего абонемента от 1 до 6 месяцев

### Средний процент оттока — 27%. Кластер 4. 
#### Выделяются тем, что не оставили номера телефонов
- Живут или работают недалеко от центра
- 47% пришли по партнерской программе
- Абонементы на 6 месяцев
- Менее половины из них посещают групповые занятия
- Частота посещений — 1,85 раз в неделю

#### По признакам, которые отметил алгоритм в порядке убывания веса 
1. Средняя частота посещений от 1.02 до 2.39 за предыдущий месяц
2. Количество месяцев с момента первого посещения от 1 до 5 месяцев
3. Средняя частота посещений в неделю за все время от 1.2 до 2.42 раз в неделю
4. Возраст 27-31
5. Длительность текущего действующего абонемента от 1 до 6 месяцев

### Высокий процент оттока — 44%. Кластер 0. 
#### Выделяются тем, что живут или работают далеко от центра
- Живут или работают далеко от центра
- 46% пришли по партнерской программе
- Абонементы на 3 месяца
- Частота посещений — 1,66 раз в неделю

#### По признакам, которые отметил алгоритм в порядке убывания веса 
1. Средняя частота посещений от 0.77 до 2.12 за предыдущий месяц
2. Количество месяцев с момента первого посещения от 1 до 4 месяцев
3. Средняя частота посещений в неделю за все время от 1.04 до 2.22 раз в неделю
4. Возраст 26-31
5. Длительность текущего действующего абонемента от 1 до 3 месяцев

### Самый высокий процент оттока — 52%. Кластер 2. Выделяются тем, то реже всех посещают занятия
- Живут или работают чуть дальше от центра
- Абонементы на 3 месяца
- Реже всех посещают групповые занятия
- Частота посещений — 1,25 раз в неделю

#### По признакам, которые отметил алгоритм в порядке убывания веса 
1. Средняя частота посещений от 0.48 до 1.47 за предыдущий месяц
2. Количество месяцев с момента первого посещения до 3 месяцев
3. Средняя частота посещений в неделю за все время от 0.77 до 1.69 раз в неделю
4. Возраст 26-30
5. Длительность текущего действующего абонемента от 1 до 3 месяцев

#### На отток влияют расзные факторы
- Проживание или работа поблизости
- Посещение групповых занятий или налиие компании для тренировок 
- Возраст клиента

# Рекомендации <a id="recomend"></a>

### Есть несколько возможных направлений
- удержание колеблющихся, кластер 4, за счет скидок на групповые занятия и комплиментов (например,скидка на вторую покупку в неделю на дополнительные услуги)
- стимуляция кластера 3, за счет предложений продления абонементов до года со скидками
- стимуляция начинающих посещать реже 1 раза в неделю — смс-напомнинание о тренировке
- привлечение новых, за счет расширения сети партнерских программ c близлежайшими офисами и домами, развитие программ скидок для членов семьи и друзей
