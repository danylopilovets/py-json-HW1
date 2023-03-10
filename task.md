Тема: Python Intro.

Дата видачі: 28.10.2022

Дата здачі: 04.11.2022

Максимальна оцінка: 100 балів

Виконання ДЗ - індивідуальне!

Результатом виконання завдання для перевірки буде посилання на гілку в gitlab репозиторії (залити посилання нижче Text reply - > Send your reply.). 



У даному завданні вам потрібно розробити програму на Python для обробки даних про користувачів. Використовуйте усі свої отримані знання із лекцій. Можете розподіляти код по функціях / модулях так, як вважаєте за потрібне. Використовуйте лише стандартні бібліотеки або ж ті, що були згадані під час лекцій.


Оцінювання:

- 80 балів за правильність роботи програми (20 за балів за кожен пункт):

    - 10 балів за правильність роботи

    - 10 балів за алгоритм (простота, швидкодія, гнучкість до змін)

- 20 балів за оформлення коду згідно стандартів



Завдання:

1. Завантажити дані про користувачів із файлу data.jsonl

Потрібно прочитати файл у форматі JSON Lines, в якому в кожному окремому рядку записаний обʼєкт у форматі JSON
Завантажити дані у вигляді списку словників
В кожному словнику сконвертувати поле time_created з числа у тип datetime
2. Видалити дублікати з даних

Дані вважаються дублікатом, якщо в них співпадають поля name та time_created
При наявності дублікатів потрібно залишати той, що записаний раніше
3. Заповнити пропуски в даних

Потрібно знайти пропущені поля у деяких словниках. Повний список необхідних полів можна отримати взявши усі унікальні ключі серед усіх словників
Пропущені поля потрібно заповнити даними за правилом:
           - Числові поля заповнити середнім значенням цього поля у користувачів

                    - Для цілочисельних значень округляти вниз

          - Для текстових значень заповнити значенням цього поля, яке зустрічається найчастіше

          -  Для інших типів записувати значення None

4. Записати трансформовані дані

Потрібно записати у декілька файлів у форматі JSON в кожному окремому рядку
Оскільки JSON не підтримує тип datetime для поля time_created, то його перед цим необхідно сконвертувати назад у тип int
Дані розподіляються по файлам відповідно до дати з поля time_created
Імʼя файла має виглядати як {year}-{month}-{day}.jsonl
Приклад


Вміст файлу 
data.json:




[


  {“name”: “Petro”, “time_created”: 1666900979, “age”: 20}, 


  {“name”: “Petro”, “time_created”: 1666900980, “city”: “Kiyv”},


  {“name”: “Vasyl”, “time_created”: 1666900979, “age”: 22},


  {“name”: “Petro”, “time_created”: 
1666804104,
“premium”: true},


  {“name”: “Petro”, “time_created”: 1666900979, “age”: 40}


]


Результат:


Файл 2022-10-27.json містить дані:

[

  {“name”: “Petro”, “time_created”: 1666900979, “age”: 21, “city”: “Kiyv”, “premium”: null}, 

  {“name”: “Petro”, “time_created”: 1666900980, “age”: 21, “city”: “Kiyv”, “premium”: null},

  {“name”: “Vasyl”, “time_created”: 1666900979, “age”: 21, “city”: “Kiyv”, “premium”: null}

]


Файл 2022-10-26.json містить дані:


[

  {“name”: “Petro”, “time_created”: 1666804104, “age”: 21, “city”: “Kiyv”, “premium”: true}

]



Пояснення до прикладу


Був видалений словник {“name”: “Petro”, “time_created”: 1666900979, “age”: 40}, оскільки він є дублікатом

Унікальними полями є name, time_created, age, city, premium. Відповідно всі словники мають містити ці поля

Середнє для поля age є 21, оскільки це середнє між 20 та 22 (40 не враховуємо, оскільки був у видаленому словнику)

Поле city заповнюється значенням Kyiv, оскільки є найчастішим

Інші поля не є числовими, а отже заповнюються значенням None
