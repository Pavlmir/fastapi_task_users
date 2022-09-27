Павел, направляю Вам тестовое задание для позиции Back-end Developer (Python):


Главная цель - понять, как человек выбирает решения/алгоритмы и каковы общие подходы (в том числе само понимание задачи).


Одно из важных условий: НЕ использовать ничего стороннего кроме основных стандартных фреймворков и утилит - никаких boilerplate code (даже свои собственные ранние наработки нежелательны). Однако, естественно, можно использовать JSON парсер и похожее фундаментальное.

Стэк:

    Python 3.7+
    Flask/FastAPI
    PostgreSQL
    SQLAlchemy/Asyncpg
    asyncio

Задание из двух частей - попроще и посложнее. Обе части можно объединить.

I. Python приложение редактирования пользователей:

    Минимум две страницы: логин и, собственно, список.
    Возможность добавлять/удалять/редактировать пользователей и их права: полные (редактирование/добавление/удаление) и только просмотр.
    Пользоваться можно только залогинившись и должно действовать ограничение прав.
    HTML с запросами через Ajax REST c JSON (простейшее JavaScript приложение - нативно или максимум jQuery) на фронтенде. Да, это не backend, но хороший разработчик будет кристально ясно понимать, что и как происходит на фронте. Можно сделать и просто на формах, Ajax лишь бонус.
    Обязательно показать использование как ORM так и raw SQL.
    Seed базы - первый пользователь с полными правами.
    Описание запуска проекта в виде: README.md
    Зависимости проекта в виде: requirements.txt
    По возможности комментарии к коду (бонус).
    Проверьте ваш проект на работоспособность - это очевидно.

II. Python, асинхронные запросы.

Можно использовать любой доступный метод для достижения “асинхронности” (concurrent computing), включая парадигмы как Reactive и т.п.

    Есть три удаленных источника данных (в качестве источников для тестового задания то могут быть два статических JSON файла на том же сервере с массивом простых данных - ID и некое текстовое поле, содержащее в теле ID).

Пример:

   [
       {“id”:1,”name”:”Test 1”},
       {“id”:2,”name”:”Test 2”}
   ]
  
Источники доступны по HTTP. В данных для каждого элемента должен быть ID.

ID распределены следующим образом:

   1-й источник: ID 1-10,31-40;
   2-й источник: ID 11-20,41-50;
   3-й источник: ID 21-30,51-60;
   
    Есть одна общая точка доступа до этих данных (приложение Flask), которая выдаёт коррелированный результат. Точка доступна по HTTP.
    Эта точка должна делать запросы ко всем источникам “асинхронно” и ждать результата со всех.
    По получению результата от всех, выдать отсортированный по ID результат (данные со всех источников).
    Ошибка от любого из источников игнорируется и интерпретируется, как отсутствие данных.
    Ошибкой также считается таймаут (2 секунды).

Общее условие: для всех решенных задач нужно сделать инструкцию по запуску из под VENV. Запуск проекта в Docker контейнерах или каким-то другим способом будет плюсом, но это не требуется.


///