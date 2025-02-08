# OkorokovaVD

__

25.01.2025

создали новую врм, 4гб операционной памяти, 2 процессора

установили гостевые дополнения


__

01.02.2025

ввели команду для установки улиты wget: __yum install wget__ (sudo yum install wget - sudo для выполнения команды под правами суперпользователя )

ОШИБКА: is not in the sudoers file

![image](https://github.com/user-attachments/assets/179d9bbc-24cd-43c2-adff-7ef5f2116a3a)

переходим в роль рута: __su root__

![image](https://github.com/user-attachments/assets/b3229764-d06f-4906-abc6-997263483bcb)

исправляем ошибку через конфигурационный файл /etc/sudoers:
__vi /etc/sudoers__

![image](https://github.com/user-attachments/assets/32b0b954-630f-4430-b8aa-910714213de3)

внутри прописали права нашему пользователю, сохранили (esc, shift+Ж wq!)

![image](https://github.com/user-attachments/assets/08bd7ea2-d2e3-475d-ac8d-1bbddbdbb34e)

после решения проблемы переходим в другое окно под нашим пользователем

вводим команду для установку улиты: __yum install wget__ (sudo yum install wget - sudo для выполнения команды под правами суперпользователя )

![image](https://github.com/user-attachments/assets/c757f47e-e1dc-49ab-b4e5-7b002caca82d)


__

08.02.2025

установка пакета curl в вашу систему: __sudo yum install curl__, пишет что уже установлен

![image](https://github.com/user-attachments/assets/ffb5a3e6-5080-4871-abc8-b4b0fa93b587)

скачиваем файл репозитория: __sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo__

![image](https://github.com/user-attachments/assets/468ad6c8-066a-429e-a11f-cda851c3dd9d)

установка docker: __sudo yum install docker-ce docker-ce-cli containerd.io__

![image](https://github.com/user-attachments/assets/78cc0abc-5e38-4e3e-a3cc-229cddd662e6)

запуск его и разрешение автозапуска: __sudo systemctl enable docker --now__

![image](https://github.com/user-attachments/assets/ee9777bd-6410-451b-949f-78f0c28e96f1)



