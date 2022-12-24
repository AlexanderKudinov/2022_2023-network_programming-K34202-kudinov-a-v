University: ITMO University
Faculty: FICT
Course: Network programming
Year: 2022/2023
Group: K34202
Author: Kudinov Alexander Vadimovich
Lab: Lab4
Date of create: 27.11.2022

Цель работы: Изучить синтаксис языка программирования P4 и выполнить 2 задания обучающих задания от Open network foundation для ознакомления на практике с P4.

Ход работы:

Вначале была установлена виртуальная машина с необходимыми средствами для выполнения заданий.

1. Задание Basic Forwarding

Был скомпилирован стартовый файл basic.p4 с помощью команды make run, после чего повяилась командная строка Mininet (Рисунок 1).

![image](https://user-images.githubusercontent.com/42407837/209434901-38c74a53-2a81-4955-8953-a204aafa4b7c.png)

Рисунок 1 - Командная строка

Далее была произведена проверка соединения с помощью команды ping, пинг между хостами в схеме не работает, потому что все пакеты автоматически отбрасываются.

![image](https://user-images.githubusercontent.com/42407837/209434914-415322b2-9270-41ed-8613-4fe9b7edf4e9.png)

Рисунок 2 - Тестирование команды ping

Были добавлены парсеры для ipv4 и ethernet загловков (Рисунок 3).

![image](https://user-images.githubusercontent.com/42407837/209434996-613647ae-e392-46d9-bccb-86e96bba0c92.png)

Рисунок 3 - Добавление парсеров

Была добавлена логика для пересылки ipv4 пакетов (Рисунок 4). При пересылке ipv4 пакетов необходимо установить выходный порт, обновить MAC адрес назначения, обновить исходный MAC адрес, а также уменьшить значение TTL на 1.

![image](https://user-images.githubusercontent.com/42407837/209435035-5305f5c7-cca0-48a9-8b1a-9c6466ba7839.png)

Рисунок 4 - Логика для пересылки ipv4 пакетов

Длаее была определена таблица, отвечающая за маршрутизацию (Рисунок 5).

![image](https://user-images.githubusercontent.com/42407837/209435051-c6623b50-ab7e-48a4-ab00-df52675a1ecf.png)

Рисунок 5 - Таблица маршрутизации

Также было добавлено условие для проверки корректности ipv4 заголовка (Рисунок 6).

![image](https://user-images.githubusercontent.com/42407837/209435061-bf388567-03b5-44d0-b7f8-2a829c439964.png)

Рисунок 6 - Проверка ipv4 заголовка

Затем была произведено добавление заголовка (Рисунок 7)

![image](https://user-images.githubusercontent.com/42407837/209435106-9c846b87-2702-4d3b-8e1a-b5cbc8db18a7.png)

Рисунок 7 - Добавление заголовка

С помощью команды ping подключение было снова проверено - на этот раз успешно (Рисунок 8).

![image](https://user-images.githubusercontent.com/42407837/209435174-96c6ecee-7d4e-4639-b45a-9965b231af93.png)

Рисунок 8 - Проверка подключения

2. Задание Basic Tunneling

Вначале был определен новый заголовок myTunnel_t (Рисунки 9 и 10).

![image](https://user-images.githubusercontent.com/42407837/209435302-897db7ed-9f8e-46a5-9e78-841f6d28cc98.png)

Рисунок 9 - Создание заголовка myTunnel_t

![image](https://user-images.githubusercontent.com/42407837/209435323-4830bd76-e551-4d84-90ee-3337f01ba4ee.png)

Рисунок 10 - Добавление заголовка myTunnel_t

Был добавлен парсер parse_myTunnel (Рисунок 11), который извлекает заголовок myTunnel. Если значение поля proto_id равно 0x800, то следует перейти на парсер parse_ipv4.

![image](https://user-images.githubusercontent.com/42407837/209435362-bc4dbc9e-fb1e-4600-add9-63e6e294efe3.png)

Рисунок 11 - Парсер parse_myTunnel

Далее парсер parse_ethernet был изменен (Рисунок 12), чтобы извлечь либо ipv4 заголовок, либо myTunnel заголовок в зависимости от значения поля etherType. Значение etherType, которое соответствует заголовку myTunnel, равно 0x1212. Это значение определено в самом начале файла.

![image](https://user-images.githubusercontent.com/42407837/209435377-70f9cd32-904a-4cf6-be48-d7424ae57d02.png)

Рисунок 12 - Изменение парсера parse_ethernet

Была определена таблица myTunnel_exact, отвечающая за маршрутизацию myTunnel пакет (Рисунок 13). Таблица вызывает функцию myTunnel_forward, которая устанавливает выходной порт для исходящих пакетов.

![image](https://user-images.githubusercontent.com/42407837/209435402-5cffe45f-d9c9-42f7-9ad7-0609b2f99c14.png)

Рисунок 13 - Таблица myTunnel_exact

![image](https://user-images.githubusercontent.com/42407837/209435457-d8ca7073-d8d6-4b9c-951c-2d283dfda99e.png)

Рисунок 14 - Функция myTunnel_forward

Была обновлена функция apply, которая использует соответствующую таблицу в зависимости от типа пакетов (Рисунок 15).

![image](https://user-images.githubusercontent.com/42407837/209435540-1a237859-26fa-467f-a60f-ee188694978f.png)

Рисунок 15 - Функция apply

Также был написан депарсер (Рисунок 16).

![image](https://user-images.githubusercontent.com/42407837/209435678-730fd7e4-1250-42d7-807e-09f10224080d.png)

Рисунок 16 - Депарсер

Для проверки были запущены хосты h1 и h2.

![image](https://user-images.githubusercontent.com/42407837/209435771-e2154342-71f0-4f3c-aa75-79977e764eaf.png)

Рисунок 17 - Запуск первого хоста

![image](https://user-images.githubusercontent.com/42407837/209435782-cff4591c-28ed-4d36-9378-7271bd3fa603.png)

Рисунок 18 - Запуск второго хоста

Далее были запущены скрипты receive.py на хосте h2 и send.py на хосте h1. При передаче пакетов типа myTunnel можно было указать любой ip адрес.

![image](https://user-images.githubusercontent.com/42407837/209435797-6e15da31-6215-4fc8-85db-ff4f3425d483.png)

Рисунок 19 - Запуск send.py

![image](https://user-images.githubusercontent.com/42407837/209435846-a021684c-adc8-451c-a4cd-cd892fc56e2d.png)

Рисунок 20 - Запуск receive.py

Ниже представлены схемы сетей, использованных в задании:

![image](https://user-images.githubusercontent.com/42407837/204137721-60ed7002-5e34-4a07-94f0-0af2202bad69.png)

Рисунок 21 - Схема Basic Forwarding

![image](https://user-images.githubusercontent.com/42407837/204137754-75d0cc4f-3bbe-43b4-8015-32e63848a660.png)

Рисунок 22 - Схема Basic Tunneling

Вывод:
В ходе выполнения лабороторной работы было изучено стандартное перенаправление пакетов, а также туннелирование. Также данные механизмы были реализованы с помозью языка P4.
