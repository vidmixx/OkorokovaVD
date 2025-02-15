# OkorokovaVD

__

__25.01.2025__

создали новую врм, 4гб операционной памяти, 2 процессора

установили гостевые дополнения


__

__01.02.2025__

ввели команду для установки улиты wget: `yum install wget` (sudo yum install wget - sudo для выполнения команды под правами суперпользователя )

ОШИБКА: is not in the sudoers file

![image](https://github.com/user-attachments/assets/179d9bbc-24cd-43c2-adff-7ef5f2116a3a)


переходим в роль рута: `su root`

![image](https://github.com/user-attachments/assets/b3229764-d06f-4906-abc6-997263483bcb)


исправляем ошибку через конфигурационный файл /etc/sudoers:
`vi /etc/sudoers`

![image](https://github.com/user-attachments/assets/32b0b954-630f-4430-b8aa-910714213de3)


внутри прописали права нашему пользователю, сохранили (esc, shift+Ж wq!)

![image](https://github.com/user-attachments/assets/08bd7ea2-d2e3-475d-ac8d-1bbddbdbb34e)


после решения проблемы переходим в другое окно под нашим пользователем

вводим команду для установку улиты: `yum install wget` (sudo yum install wget - sudo для выполнения команды под правами суперпользователя )

![image](https://github.com/user-attachments/assets/c757f47e-e1dc-49ab-b4e5-7b002caca82d)


__

__08.02.2025__

установка пакета curl в вашу систему: `sudo yum install curl`, пишет что уже установлен

![image](https://github.com/user-attachments/assets/ffb5a3e6-5080-4871-abc8-b4b0fa93b587)


скачиваем файл репозитория: `sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/468ad6c8-066a-429e-a11f-cda851c3dd9d)


установка docker: `sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/78cc0abc-5e38-4e3e-a3cc-229cddd662e6)


запуск его и разрешение автозапуска: `sudo systemctl enable docker --now`

![image](https://github.com/user-attachments/assets/ee9777bd-6410-451b-949f-78f0c28e96f1)

__

__15.02.2025__

обновление переменной COMVER (получена в результате запроса curl, содержит в себе носер последней версии Docker Compose)
`COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

![image](https://github.com/user-attachments/assets/a6473bcf-3310-4f0e-b2b5-0b62eb0055ba)


скачиваем скрипт последней версии, используя объявленную ранее переменную и помещая скрипт в каталогг /usr/bin/docker-compose
`sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose`

![image](https://github.com/user-attachments/assets/6dcf6c85-e096-42ca-a47b-1e321140a3a3)


предоставление прав на выполнение файла docker-compose: `sudo chmod +x /usr/bin/docker-compose`

![image](https://github.com/user-attachments/assets/21f2dfb9-0470-490a-8402-30481d514168)


вывод версия: `docker-compose --version`

![image](https://github.com/user-attachments/assets/b3291feb-57c0-4c88-b646-3a084550d410)


установка гит: sudo yum install git 

![image](https://github.com/user-attachments/assets/3b1c3249-0614-4b39-96d7-3a83963668d5)


`git clone https://github.com/skl256/grafana_stack_for_docker.git`

![image](https://github.com/user-attachments/assets/9097ba2b-23af-4db1-bccf-6a5eb038c6b8)


переходим в папку: 

![image](https://github.com/user-attachments/assets/49539404-b6e8-4089-bc87-3ffd64d9be1d)

                                            
создаем полный путь  

![image](https://github.com/user-attachments/assets/5381f449-c7b1-4672-a2fc-f251c7580e54)



