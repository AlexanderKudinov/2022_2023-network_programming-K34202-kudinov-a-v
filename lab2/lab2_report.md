University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)
Year: 2022/2023
Group: K34202
Author: Kudinov Alexander Vadimovich
Lab: Lab2
Date of create: 20.11.2022
Date of finished: 

Тема: 
С помощью Ansible настроить несколько сетевых устройств и собрать информацию о них. Правильно собрать файл Inventory.

Ход работы:
Вначале была создана вторая виртуальная машина, на которую была установлена ОС RouterOS. 
Далее по аналогии с первой лабораторной работой на удаленной виртуальной машине были получены сертификаты для второго клиента и импортированы на него с помощью графического интерфейса WinBox.
Также удалось успешно подключить соединение между вторым клиентом и удаленной виртуальной машины с помощью OpenVPN.

Далее была проделана работа с Ansible. 
Вначале был создан файл hosts с конфигурацией созданных ранее виртуальных машин с RouterOS, содержащую IP, логин и пароль (Рисунок 1).

