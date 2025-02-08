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

