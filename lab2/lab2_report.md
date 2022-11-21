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
Вначале был создан файл hosts в директории /etc/ansible с конфигурацией созданных ранее виртуальных машин с RouterOS, содержащую IP, логин и пароль (Рисунок 1).

![image](https://user-images.githubusercontent.com/42407837/202906882-114bae1e-cf26-48b9-961c-ecfcba4dab44.png)

Рисунок 1 - Создание файла hosts

Затем в директории /etc/ansible был создан файл ansible_test.yml для тестирования ansible (Рисунок 2) и файл changePass.yml для настройки логина и пароля на двух виртуальных машинах с RouterOS (Рисунок 3).

![image](https://user-images.githubusercontent.com/42407837/202907934-68022514-6340-4e49-bb87-91de72c487b1.png)

Рисунок 2 - Создание файла ansible_test.yml

![image](https://user-images.githubusercontent.com/42407837/202910731-a56e5311-b380-4aed-abe8-f5297a29f813.png)

Рисунок 3 - Создание файла changePass.yml
