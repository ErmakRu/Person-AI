# Метод персонификации игрового искуственного интеллекта под темперамент игрока
Программная реализация метода магистарской ВКР ИТМО ШРВ Ермакова А.А. 
Ссылка на текст работы https://docs.google.com/document/d/1niXv35P6mhNus_G0yreSxPcXIIXYMoybxX1nH9chVSc/edit?usp=sharing
Данный файл описывает устройство проекта на Яндекс.Диске по ссылке https://disk.yandex.ru/d/JsSNb5gfEhmeHA 
Также билд игры можно найти на Itch.io по ссылке https://ermakru.itch.io/researchgame
При запуске проекта появляется пустой уровень. При запуске игроку откроется главное меню. В главное меню есть 3 кнопки:
1)	New Game. Удаляет имеющееся сохранение, после чего запускает игру с 1 уровня (Arena).
2)	Person Game. Проверяет есть ли прогресса игрока на данном компьютере, если данные есть, то открывает уровень с персонифицируемым противниками.
3)	Quit. Выход из игры.

# Сбор данных
Для сбора данных используются 4 уровня: Arena, Arena1, Arena2 и Arena3. Внутри персонажа (BP_PlayerCharacter) записаны все необходимые переменные. На каждом уровне, кроме Arena, 7 противников, при этом на Arena2 есть невидимая коллизия, пройдя через которую у игрока меняется местами кнопки атаки и защиты. Противники на каждом уровне не отличаются друг от друга и нужны для сбора данных о привычном способе сражения игрока, а их количество обусловлено необходимостью избавленя от статистических выбросов. В конце уровня, при захождении в коллизию телепорта (BP_OpenLevel) на следующий уровень, все переменные переписываются в файл на компьютере, который расположен по пусти C/ResearchGame/*Название текущего уровня*.  
![image](https://github.com/ErmakRu/Person-AI/assets/113769680/f819d201-6ddb-497c-b147-ae74c6dd9742)

При захождении телепорт в Arena3, данные из игры записываются в папку Arena 3, затем все данные из файлов Arena1-Arena3 суммируются и записываются в ArenaFinal, после чего игроку показывается финальный экран с значениями из игры. На финальном экране есть ссылка на прохождения теста на темперамент с передачей данных в таблицы.
![image](https://github.com/ErmakRu/Person-AI/assets/113769680/955cdd85-5db5-4fff-9259-7c5257c36e45)

# Изменение данных
Для того чтобы запустить персонифицированных ИИ нужно открыть ArenaFinal, проходя через дверь, противник меняет свой Behavior Tree. Все Behavior Tree можно найти в папке Content\FlexibleCombatSystem\Blueprints\AI там же есть дверь изменяющая древо поведения.
![image](https://github.com/ErmakRu/Person-AI/assets/113769680/4fc1319c-3df3-4313-9101-15160c970f09)

Название всех Behavior Tree имеют в своем названии темперамент к которому относится данное древо. A – обозначает активность, а E – эмоциональность, цифры 1,2 и 3 обозначаются низкий, средний и высокий уровень по Русалову соответственно. К примеру название BT_AI_A2E3 обозначает что данное древо переназначено для людей с средней (2) активностью и высокой (3) эмоциональностью. 
Изменение переменных, влияющих на определение темперамента можно изменить в BP_Change_BT, указав иной файл загрузки из ArenaFinal и другие значения показателя 

