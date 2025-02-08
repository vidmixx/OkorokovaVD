# OkorokovaVD

__

25.01.2025

создали новую врм, 4гб операционной памяти, 2 процессора

установили гостевые дополнения


__

01.02.2025

ввели команду для установки улиты wget: yum install wget (sudo yum install wget - sudo для выполнения команды под правами суперпользователя )

ОШИБКА: is not in the sudoers file

![image](https://github.com/user-attachments/assets/179d9bbc-24cd-43c2-adff-7ef5f2116a3a)

переходим в роль рута: su root

![image](https://github.com/user-attachments/assets/b3229764-d06f-4906-abc6-997263483bcb)

исправляем ошибку через конфигурационный файл /etc/sudoers
vi /etc/sudoers

![image](https://github.com/user-attachments/assets/32b0b954-630f-4430-b8aa-910714213de3)

внутри прописали права нашему пользователю, сохранили (esc, shift+Ж wq!)

![image](https://github.com/user-attachments/assets/08bd7ea2-d2e3-475d-ac8d-1bbddbdbb34e)

после решения проблемы переходим в другое окно под нашим пользователем

вводим команду для установку улиты: yum install wget (sudo yum install wget - sudo для выполнения команды под правами суперпользователя )

![image](https://github.com/user-attachments/assets/c757f47e-e1dc-49ab-b4e5-7b002caca82d)


__

08.02.2025

устанавливает утилиту wget на вашу систему

![image](https://github.com/user-attachments/assets/ffb5a3e6-5080-4871-abc8-b4b0fa93b587)

скачиваем файл репозитория

![image](https://github.com/user-attachments/assets/468ad6c8-066a-429e-a11f-cda851c3dd9d)

Устанавливаем docker

![image](https://github.com/user-attachments/assets/78cc0abc-5e38-4e3e-a3cc-229cddd662e6)

Запускаем его и разрешаем автозапуск

![image](https://github.com/user-attachments/assets/ee9777bd-6410-451b-949f-78f0c28e96f1)



