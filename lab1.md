University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)
Year: 2022/2023
Group: K34202
Author: Kudinov Alexander Vadimovich
Lab: Lab1
Date of create: 19.11.2022
Date of finished: 

Тема: Установка CHR и Ansible, настройка VPN
Цель работы: развертывание виртуальной машины на базе платформы Microsoft Azure с установленной системой контроля конфигураций Ansible и установка CHR в VirtualBox.

Ход работы:
Вначале был создан аккаунт в Яндекс Облаке, где была создана виртуальная машина с операционной системой Linux Ubuntu 20.04 (Рисунок 1)

![image](https://user-images.githubusercontent.com/42407837/202846613-76f4bf5d-5ecd-4b3a-b9e6-292a4a6e8c69.png)

Рисунок 1 - Создание виртуальной машины

Далее было произведено подключение к созданной ранее виртуальной машине с помощью команды ssh (Рисунок 2)

![image](https://user-images.githubusercontent.com/42407837/202846940-90410c04-11e3-415d-bce6-62601b8bc7bd.png)

Рисунок 2 - Подключение к виртуальной машине

Затем был установлен python3 и Ansible (Рисунок 3)

![image](https://user-images.githubusercontent.com/42407837/202847680-66c85288-b024-497a-b48c-0340f871d75c.png)

Рисунок 3 - Установка Ansible

Далее был установлен OpenVPN.

После этого был установлен VirtualBox, и создана виртуальная машина, на которую был установлен Router OS 7 (Рисунок 4).

![image](https://user-images.githubusercontent.com/42407837/202852090-7bb4407b-7f77-4322-b01a-abb764a408c0.png)

Рисунок 4 - Установка Router OS 7

Затем был установлен WinBox и подключен к клиенту. В файловую систему были добавлены сертификаты OpenVPN, полученные с сервера (Рисунок 5), затем данные сертификаты были импортированы (Рисунок 6).

![image](https://user-images.githubusercontent.com/42407837/202854476-3c4acd3e-20bb-4c34-b71b-ec7c1473f073.png)

Рисунок 5 - Добавление сертификатов OpenVPN

![image](https://user-images.githubusercontent.com/42407837/202856301-c7147b2f-8bac-4ac9-9b9e-27c5f775dac6.png)

Рисунок 6 - Импорт сертификатов OpenVPN

Далее был настроен VPN туннель между сервером и клиентом (Рисунок 7 и рисунок 8).

![image](https://user-images.githubusercontent.com/42407837/202856471-7765369e-fea4-4a99-904d-f4347a948ebb.png)

Рисунок 7 - Настройка VPN туннеля

![image](https://user-images.githubusercontent.com/42407837/202860977-365ef1bc-8179-446f-9acd-eba5f562826c.png)

Рисунок 8 - Настройка VPN туннеля

В результате с клиента получилось "пропинговать" сервер (Рисунок 9), значит,VPN-туннель работает корректно.

![image](https://user-images.githubusercontent.com/42407837/202861123-9b265533-fc77-41dc-98a4-224f80bb59c2.png)

Рисунок 9 - Проверка работы VPN-туннеля


