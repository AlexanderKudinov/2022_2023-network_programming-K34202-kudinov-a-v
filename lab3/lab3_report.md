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

Вначале был поднят Ubuntu на новой виртуальной машине. По аналогии со второй лабороторной работой данная виртуальная машина была соединена с вритуальной машиной, размещенной в облаке Яндекса, используя OVPN туннель.

Затем был установлен и запущен Postgresql с помощью следующих команд:

sudo apt update
sudo apt install -y postgresql
sudo systemctl start postgresql
sudo systemctl enable postgresql

Далее был установлен Reddis, а также была создана база данных для Netbox. Затем была склонирована ветка репозитория NetBox из GitHub. Но перед этим была установлена команда git, поскольку ее не оказалось на виртуальной машине.

Далее была создана системная учетная запись пользователя с именем Netbox с помощью следующих команд:
sudo adduser --system --group netbox
sudo chown --recursive netbox /opt/netbox/netbox/media/

Затем была создана виртуальная среда Python, а также был создан суперпользователь для авторировации в Netbox. Наконец, сервер Netbox был поднят на порту 8000 (Рисунок 1).

![image](https://user-images.githubusercontent.com/42407837/209433674-792a8f2a-953f-44e9-b153-c17c0abb4030.png)

Рисунок 1 - Поднятие сервера Netbox

Был установлен и запущен nginx, после чего Netbox был открыт через браузер (Рисунок 2).

![image](https://user-images.githubusercontent.com/42407837/209428090-e3bf0080-d4f8-4e3f-95f0-8da3a8e7f543.png)

Рисунок 2 - Подключение к Netbox

Затем была внесена информация о двух роутерах (Рисунки 3 и 4). Для внесения IP адреса пришлось создать интерфейсы.

![image](https://user-images.githubusercontent.com/42407837/209433770-6e9c5a38-5c06-44e3-bbe0-fc4c68ecaaaf.png)

Рисунок 3 - Внесение информации о первом CHR

![image](https://user-images.githubusercontent.com/42407837/209433794-8797baa9-0c75-4fb6-87a5-e759505e71a9.png)

Рисунок 4 - Внесение информации о втором CHR

Затем было произведено соединение Netbox VM с Wireguard сервером, который находится на Яндексе (Рисунки 5 и 6).

![image](https://user-images.githubusercontent.com/42407837/209433864-1fb58eb1-5175-476b-a10c-821421d906d0.png)

Рисунок 5 - Соединение Netbox VM с Wireguard сервером

![image](https://user-images.githubusercontent.com/42407837/209433875-6ec29d1d-aa53-4ba6-8c29-3944972a8e98.png)

Рисунок 6 - Соединение Netbox VM с Wireguard сервером

Далее был создан файл hosts (Рисунок 7)

![image](https://user-images.githubusercontent.com/42407837/209433909-9bed39f3-b77c-4e5f-8f5b-138d4c700627.png)

Рисунок 7 - Файл hosts

Затем был создан API токен (Рисунок 8)

![image](https://user-images.githubusercontent.com/42407837/209433974-c9e6c218-2c53-4db2-ba26-1f2ac6f8eab1.png)

Рисунок 8 - API токен

Был создан файл файл netbox_data.yml, чтобы сохранить все данные из Netbox в текстовый файл.

![image](https://user-images.githubusercontent.com/42407837/209434017-f210d13a-7251-4cc9-898f-fda74af9ffb9.png)

Рисунок 8 - файл netbox_data.yml

Далее было произведено сохранение всех данных о наших CHR из Netbox, используя Ansible (Рисунки 9 и 10).

![image](https://user-images.githubusercontent.com/42407837/209434088-bf3a1bde-2727-49d4-9350-512303b43673.png)

Рисунок 9 - Сохранение данных с помощью Ansible

![image](https://user-images.githubusercontent.com/42407837/209434158-cf90182c-81a6-4341-bc5a-411ff961799a.png)

Рисунок 10 - Результат

Был написан сценарий, при котором на основе данных из Netbox можно настроить 2 CHR, изменить имя устройства, добавить IP адрес на устройство (Рисунок 11), далее данный сценарий был запущен (Рисунок 12).

![image](https://user-images.githubusercontent.com/42407837/209434253-339004d9-85ec-40de-b277-0143b9fe1ce3.png)

Рисунок 11 - Файл name_IP.yml

![image](https://user-images.githubusercontent.com/42407837/209434263-8b1b06a2-9ef6-4ab0-bd9f-b62bc2752aca.png)

Рисунок 12 - Запуск сценария

Был написан сценарий для сбора серийного номера устройства и записи серийного номера в Netbox (Рисунок 13), затем данный сценарий был запущен (Рисунок 14).

![image](https://user-images.githubusercontent.com/42407837/209434293-8f04b76b-77f3-4721-89c7-ec0de3a61f52.png)

Риунок 13 - Файл set_serial_number.yml

![image](https://user-images.githubusercontent.com/42407837/209434301-771a3bd9-e845-45e4-ac36-8d78335c18dc.png)

Рисунок 14 - Запуск сценария

В результате серийный номер добавлен в Netbox (Рисунки 15 и 16).

![image](https://user-images.githubusercontent.com/42407837/209434323-e41c6c39-820d-47c3-8f90-b4b7a92539f6.png)

Рисунок 15 - Результат добавления серийного номера

![image](https://user-images.githubusercontent.com/42407837/209434325-deca8ccf-36c8-48e7-9b61-ae88c2cd54d5.png)

Рисунок 16 - Результат добавления серийного номера (2)

Ниже представлена схема связи (Рисунок 17)

![image](https://user-images.githubusercontent.com/42407837/209434360-31ada486-de2c-40f0-9f78-36e7c2ed0c23.png)

Рисунок 17 - Схема связи

Наконец, была произведена проверка подключения (Рисунок 18), подключение выполнилось успешно.

![image](https://user-images.githubusercontent.com/42407837/209434384-33f22db2-8416-4525-975c-fff3bc22c33a.png)

Рисунок 18 - Проверка подключения

Вывод: 
В результате выполнения лабороторной работы было произведено ознакомление с достаточно гибким инструментом для документирования сетей - Netbox. Также с помощью Netbox и Ansible были настроены оба CHR.
