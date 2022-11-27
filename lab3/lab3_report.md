University: ITMO University
Faculty: FICT
Course: Network programming
Year: 2022/2023
Group: K34202
Author: Kudinov Alexander Vadimovich
Lab: Lab3
Date of create: 27.11.2022
Date of finished:

Цель: С помощью Ansible и Netbox собрать всю возможную информацию об устройствах и сохранить их в отдельном файле.

Ход работы:

Вначале был поднят Ubuntu 20.04 на новой виртуальной машине. По аналогии со второй лабороторной работой данная виртуальная машина была соединена с вритуальной машиной, размещенной в облаке Яндекса, используя OVPN туннель.

Затем был установлен и запущен Postgresql с помощью следующих команд:

sudo apt update
sudo apt install -y postgresql
sudo systemctl start postgresql
sudo systemctl enable postgresql

![image](https://user-images.githubusercontent.com/42407837/204133376-cfdac721-29ca-41b9-b4c9-240f2c90a4e9.png)

Рисунок 1 - Установка Postgresql.

Затем была создана база данных для Netbox (Рисунок 2).

![image](https://user-images.githubusercontent.com/42407837/204133591-2cd93ac7-cc46-48e0-9263-4691d8966ab1.png)

Рисунок 2 - Создание базы данных

Далее был установлен Reddis, а также Netbox (Рисунки 3 и 4).

![image](https://user-images.githubusercontent.com/42407837/204133690-cf2ac012-537c-43e7-a930-6ee9c201ce94.png)

Рисунок 3 - Установка Reddis

![image](https://user-images.githubusercontent.com/42407837/204133933-7eddf55f-5ee2-407f-a3bc-33ca24b9e4cf.png)

Рисунок 4 - Установка Netbox

Затем была склонирована ветка репозитория NetBox из GitHub. Но перед этим была установлена команда git, поскольку ее не оказалось на виртуальной машине (Рисунок 5).


Рисунок 5 - Клонирование репозитория Netbox

Далее была создана системная учетная запись пользователя с именем Netbox с помощью следующих команд:
sudo adduser --system --group netbox
sudo chown --recursive netbox /opt/netbox/netbox/media/

Затем была создана виртуальная среда Python, а также был создан суперпользователь для авторировации в Netbox. Наконец, сервер Netbox был запущен.

Был установлен и запущен nginx, после чего Netbox был открыт через браузер (Рисунок 6).

![image](https://user-images.githubusercontent.com/42407837/204134402-9354f59c-9901-46f0-b4bb-7bf778b62474.png)

Рисунок 6 - Подключение к Netbox
