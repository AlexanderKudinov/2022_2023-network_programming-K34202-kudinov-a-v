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

Вначале с помощью Vagrant была установлена виртуальная машина (Рисунок 1).

![image](https://user-images.githubusercontent.com/42407837/204136675-0fec33a4-b0e0-44e8-825a-e17140a0012a.png)

Рисунок 1 - Установка виртуальной машины с помощью Vagrant

Затем с помощью Makefile была выполнена превичная конфигурация сети "Basic Forwarding", а также проверена связь хостов через команду "ping" - все 100% пакетов были потеряны (Рисунок 1).

![image](https://user-images.githubusercontent.com/42407837/204137044-c0214ba5-97af-4d77-9de4-fa80d3bfa57e.png)

Рисунок 2 - Тестирование команды ping

Далее был отредактирован файл basic.p4 для корректной работы сети (Рисунки 3-5).

![image](https://user-images.githubusercontent.com/42407837/204136915-03e6fc88-d004-4cde-b4c0-72e7c55a301a.png)

Рисунок 3 - Добавление парсинга Ethernet

![image](https://user-images.githubusercontent.com/42407837/204136943-bd2ef81c-9d67-406b-b7de-c241d8a70687.png)

Рисунок 4 - Добавление логики пеерсылки ipv4 пакетов

![image](https://user-images.githubusercontent.com/42407837/204136967-b3a1bc28-4901-4a2b-9576-e65a293214de.png)

Рисунок 5 - Добавление валидации пакетов

Затем с помощью с помошью Makefile и исправленного basic.p4 сеть была заново сконфигурирована. Команда ping была протестирована заново - в этот раз все 100% пакетов были доставлены (Рисунок 6).

![image](https://user-images.githubusercontent.com/42407837/204137003-7c45db04-c940-402f-92e0-fb7b4fe643a9.png)

Рисунок 6 - Тестирование команды ping

Был отредактирован файл basic_tunnel.p4 для корректной работы сети "Basic Tunneling" (Рисунки 7-8).

![image](https://user-images.githubusercontent.com/42407837/204137176-221a91fe-34ee-4662-8334-c7dc42c9bb76.png)

Рисунок 7 - Добавление парсинга myTunnel хэдеров

![image](https://user-images.githubusercontent.com/42407837/204137218-f98b1760-5e51-4343-8037-7712906c6804.png)

Рисунок 8 - Добавление логики пересылки myTunnel пакетов

Затем с помощью с помошью Makefile и исправленного basic_tunnel.p4 сеть была заново сконфигурирована. Команда ping была протестирована заново - в этот раз все 100% пакетов были доставлены (Рисунок 9).

![image](https://user-images.githubusercontent.com/42407837/204137368-20cef349-b412-493c-9636-2e42ff0a9861.png)

Рисунок 9 - Тестирование команды ping

Наконец, работа сети была проверена через программы receive.py и send.py. Также была проверена работоспособность туннелирования с помощью параметра dst_id (Рисунки 10-15).

![image](https://user-images.githubusercontent.com/42407837/204137548-6c7f1cc4-3cff-450f-98a9-712bddf8089a.png)

Рисунок 10 - Тестирование receive.py (1)

![image](https://user-images.githubusercontent.com/42407837/204137587-4bd1c215-a4e6-4106-b537-75509f5b2624.png)

Рисунок 11 - Тестирование send.py (1)

![image](https://user-images.githubusercontent.com/42407837/204137633-bdd321aa-1d34-460b-9715-623df003e5e6.png)

Рисунок 12 - Тестирование receive.py (2)

![image](https://user-images.githubusercontent.com/42407837/204137645-c2926f5c-ed97-4f37-b7b0-0da0dd6ef95c.png)

Рисунок 13 - Тестирование send.py (2)

![image](https://user-images.githubusercontent.com/42407837/204137663-822ac5b8-9667-4358-8393-40b55006bdb2.png)

Рисунок 14 - Тестирование receive.py (3)

![image](https://user-images.githubusercontent.com/42407837/204137677-8ebedd2a-5675-481d-ba65-af07f3f71efc.png)

Рисунок 15 - Тестирование send.py (3)

Ниже представлены схемы сетей, использованных в задании

![image](https://user-images.githubusercontent.com/42407837/204137721-60ed7002-5e34-4a07-94f0-0af2202bad69.png)

Рисунок 16 - Схема Basic Forwarding

![image](https://user-images.githubusercontent.com/42407837/204137754-75d0cc4f-3bbe-43b4-8015-32e63848a660.png)

Рисунок 17 - Схема Basic Tunneling

Вывод:
В ходе выполнения лабороторной работы было изучено стандартное перенаправление пакетов, а также туннелирование. Также данные механизмы были реализованы с помозью языка P4.
