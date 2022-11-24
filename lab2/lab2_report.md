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

Затем в директории /etc/ansible был создан файл ansible_test.yml (Рисунок 2), а затем была протестирована работоспособность ansible (Рисунок 3).

![image](https://user-images.githubusercontent.com/42407837/202978862-a2683207-b010-4dfa-a36b-354c9a7c3874.png)

Рисунок 2 - Создание файла ansible_test.yml

![image](https://user-images.githubusercontent.com/42407837/203728961-4211a439-0f29-4c7b-bcb7-717ad7972243.png)

Рисунок 3 - Тестирование ansible

Затем был создан файл changePass.yml (Рисунок 4), и настроен логин и пароль на двух виртуальных машинах с RouterOS.

![image](https://user-images.githubusercontent.com/42407837/202910731-a56e5311-b380-4aed-abe8-f5297a29f813.png)

Рисунок 4 - Создание файла changePass.yml

Далее с помощью Ansible были настроены NTP-клиенты (Рисунок 5), а также OSPF роутинг (Рисунок 6) сразу на двух виртуальных машинах с RouterOS. Результат работы представлен на рисунке 7.

![image](https://user-images.githubusercontent.com/42407837/203729422-baf03aba-521a-4f5e-aa8e-9ca05be3af52.png)

Рисунок 5 - Настройка NTP-клиентов

![image](https://user-images.githubusercontent.com/42407837/203729734-beb1ae7e-5480-48e6-bcf8-316a2ffb0789.png)

Рисунок 6 - Настройка OSPF роутинга

![image](https://user-images.githubusercontent.com/42407837/203730025-d6415d72-20a4-4b01-8bd4-f24b0fefaeff.png)

Рисунок 7 - Результат работы

Затем с помощью Ansible были собраны данные по OSPF топологии и полный конфиг устройства сразу на двух виртуальных машинах с RouterOS, после чего результаты были сохранены в файлах r1.json и r2.json. Содержание файла collectInfo.yml представлено на рисунке 8. 

![image](https://user-images.githubusercontent.com/42407837/203730465-20c8b54a-8d0e-4ba1-b21d-86aa0bb7d853.png)

Рисунок 8 - сбор данных по OSPF топологии
