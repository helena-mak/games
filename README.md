# Аналитика данных мобильной игры
В ходе проекта были следующие задачи 
- проанализировать результаты АВ тестирования и определить, какой набор акционных предложений для игроков можно внедрить;
- автоматизировать расчет Retention игроков;
- продумать продуктовые метрики, которые помогут оценивать результаты разных игровых событий.
## Технический стек
pandas, requests, matplotlib, scipy, requests, pingouin

## Этапы работы
1. Загрузка данных через API Yandex.
2. Предобработка данных - работа с датами, проверка на пропущенные значения, распределение данных.
3. Реализовала функции для расчета Retention и ее тестирование: 
   - функция принимает на вход датафрейм с регистрациями и авторизациями пользователей, дату начала отсчета когорт и дату окончания;
   - рассчитывает когорты и формирует сводную таблицу, которая позволяет для каждой когорты оценить Retention в порядковый день активности;
   - с помощью библиотеки seaborn формирует визуализацию heatmap.
4. Проанализировала результаты AB тестирования, в котором двум группам пользователей предлагались различные наборы акционных предложений:
   - предварительный анализ данных -  данные содержат 404 770 записей, с информацией об id пользователей, размере выручки с пользователя и к какой группе принадлежит пользователь - контрольной или тестовой;
   - распределение данных в двух группах, количество пользователей в каждой группе;
   - определение и анализ метрик для оценки качества - ARPU средний доход на каждого пользователя; ARPPU средний доход на каждого платящего пользователя; Конверсия в платящего пользователя;
   - статистические тесты для сравнения метрик в двух группах - хи-квадрат, bootstrap.
5. Разработала набор продуктовых метрик для оценки результатов игровых событий с двумя разными механиками:
   - с выдачей награды за пройденный уровень;
   - с потерей уровня при неудачной попытке прохождения.
  
## Результаты
1. Реализована функция, которая считает Retention, и выводит результат в виде таблицы и heatmap
   ![image](https://github.com/user-attachments/assets/ef29add8-ccea-45d8-892e-e3af7714fbe3)
2. Выводы по анализу акционных предложений и их влияния на продуктовые метрики:
   - ARPU в тестовой группе выше ARPU контрольной группы на 5.27%. ARPPU в тестовой группе выше ARPPU контрольной группы на 12.76%. Но статистические тесты показали, что значения метрик в каждой группе не отчилаются друг от друга.
   - конверсия в контрольной группе выше, чем конверсия в тестовой примерно на 6.64%
   - акционные предложения не влияют на размер выручки, они требуют доработки и на данный момент не могут быть внедрены для всех пользователей
   - в тестовой группе есть выбросы, которые повлияли на размер среднего чека в сторону увеличения - их стоит дополнительно проанализировать, выявить причину их появления только в одной группе
3. Набор продуктовых метрики для 2 сценарией (9 и 10 метрик) 
   
