## 25.01.2025

### Создание и запуск ВРМ, установка гост.доп

создали новую врм

* образ: oracle linux
  
* 4гб операционной памяти
  
* 2 процессора

установили гостевые дополнения

---

## 01.02.2025

### Установка wget

ввели команду для установки улиты wget (*sudo* для выполнения команды под правами суперпользователя): 

`sudo yum install wget`

__ОШИБКА:__ is not in the sudoers file

![image](https://github.com/user-attachments/assets/179d9bbc-24cd-43c2-adff-7ef5f2116a3a)

---

1. перереключаемся на суперпользователя: 

`su root`

![image](https://github.com/user-attachments/assets/b3229764-d06f-4906-abc6-997263483bcb)

---

2. открываем конфигурационный файл /etc/sudoers:

`vi /etc/sudoers`

![image](https://github.com/user-attachments/assets/32b0b954-630f-4430-b8aa-910714213de3)

---

3. внутри прописываем права нашему пользователю __okorokova ALL=(ALL)  ALL__, сохранили (esc -> shift+: -> wq!)

![image](https://github.com/user-attachments/assets/08bd7ea2-d2e3-475d-ac8d-1bbddbdbb34e)

---

после решения проблемы переходим в другое окно под нашим пользователем

снова вводим команду для установку улиты: 

`sudo yum install wget` 

![image](https://github.com/user-attachments/assets/c757f47e-e1dc-49ab-b4e5-7b002caca82d)

---

## 08.02.2025

### Установка curl

*__Curl__ это инструмент для передачи данных с сервера или к серверу через URL*

установка пакета curl в вашу систему: 

`sudo yum install curl` 

__пишет что уже установлен__

![image](https://github.com/user-attachments/assets/ffb5a3e6-5080-4871-abc8-b4b0fa93b587)

---

### Добавление репозитория Docker

чтобы установить актуальную версию Docker, необходимо добавить официальный репозиторий Docker в систему, скачиваем файл репозитория:

`sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/468ad6c8-066a-429e-a11f-cda851c3dd9d)

---

### Установка Docker 

приступаем к установке Docker,соглашаемся со всем __y__:

`sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/78cc0abc-5e38-4e3e-a3cc-229cddd662e6)

---

### Запуск службы Docker

включен автозапуск службы Docker при загрузке системы:

`sudo systemctl enable docker --now`

__подробно:__

* systemctl — это утилита для управления системными службами в Linux

* enable — добавляет службу в автозапуск, чтобы она автоматически запускалась при загрузке системы

* --now — дополнительно к enable сразу запускает службу Docker (так же как и systemctl start docker)

![image](https://github.com/user-attachments/assets/ee9777bd-6410-451b-949f-78f0c28e96f1)

---

## 15.02.2025

### Обновление и скачивание последней версии Docker Compose

1. обновление переменной COMVER (получена в результате запроса curl, содержит в себе носер последней версии Docker Compose)

`COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

![image](https://github.com/user-attachments/assets/a6473bcf-3310-4f0e-b2b5-0b62eb0055ba)

---

2. скачиваем скрипт последней версии, используя объявленную ранее переменную и помещая скрипт в каталогг /usr/bin/docker-compose

`sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose`

__подробно:__
  
* COMVER: Версия, полученная на предыдущем шаге.
  
* $(uname -s): Операционная система (например, Linux).

* $(uname -m): Архитектура процессора (например, x86_64).

* сайл сохраняется в /usr/bin/docker-compose.

![image](https://github.com/user-attachments/assets/6dcf6c85-e096-42ca-a47b-1e321140a3a3)

---

3. предоставление прав на выполнение файла docker-compose:

`sudo chmod +x /usr/bin/docker-compose`

![image](https://github.com/user-attachments/assets/21f2dfb9-0470-490a-8402-30481d514168)

---

4. вывод нынешней установленной версии: 

`docker-compose --version`

![image](https://github.com/user-attachments/assets/b3291feb-57c0-4c88-b646-3a084550d410)

---

### Клонирование репозитория с конфигурацией Grafana

1. установка Git через системный менеджер пакетов: 

`sudo yum install git`

![image](https://github.com/user-attachments/assets/3b1c3249-0614-4b39-96d7-3a83963668d5)

---

2. клонируем репозиторий с конфигурацией Grafana:

`git clone https://github.com/skl256/grafana_stack_for_docker.git`

![image](https://github.com/user-attachments/assets/9f6272b6-76f7-47fd-adfb-46a43d046476)


---

3. переход в склонированный каталог: 

`cd grafana_stack_for_docker`

---

### Подготовка директорий и файлов конфигурации 

1. создаем полный путь: 

__подробно:__

`sudo mkdir -p /mnt/common_volume/swarm/grafana/config`

* mkdir: создает новую директорию.

* -p: если родительские директории не существуют, они также будут созданы.

* /mnt/common_volume/swarm/grafana/config: путь к новой директории, которая будет создана.

---

2. создаем структуру каталогов для grafana и связанных с ней компонентов: 

`sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`

__подробно:__ 

* команда создает три директории внутри /mnt/common_volume/grafana/: grafana-config, grafana-data, prometheus-data
* {} используется для создания нескольких директорий одним вызовом mkdir.

---

3. все файлы и каталоги в указанных директориях будут переданы в собственность текущему пользователю и его группе: 

`sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}`

__подробно:__

* chown: изменяет владельца файла или директории

* -R: рекурсивно применяет изменения ко всем файлам и поддиректориям

* $(id -u): возвращает UID текущего пользователя

* $(id -g): возвращает GID группы текущего пользователz

* {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}: список директорий, для которых меняется владелец.

---

4. создаем пустой файл или обновляем аременные метки: файл grafana.ini уже существует, команда обновит его временные метки (время последнего доступа и изменения).
   
`touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

__подробно__

* touch: создает новый пустой файл (или обновляет метку времени существующего файла)
  
* /mnt/common_volume/grafana/grafana-config/grafana.ini: путь к новому файлу

---

5. копируем все файлы и подкаталоги из директории config в директорию /mnt/common_volume/swarm/grafana/config/:

`cp config/* /mnt/common_volume/swarm/grafana/config/`

__подробно__

* cp: копирует файлы
  
* config/*: все файлы из директории config
  
* /mnt/common_volume/swarm/grafana/config/: целевая директория, куда будут скопированы файлы

---

6. команда переименовывает файл grafana.yaml в docker-compose.yaml, ничего не покажет, но можно проверить при помощи команды __ls__:

`mv grafana.yaml docker-compose.yaml`

![image](https://github.com/user-attachments/assets/3280945e-30ce-400f-8ff1-90d9cecd413c)


---

7. запускаем контейнеры Docker в фоновом режиме:

`sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/bdd96786-fc0a-4e7d-87c2-a47e2bac0102)


---

## 22.02.2025

### Конфигурационный файл через VI: открыть, закрыть

зашли в файл: 

`vi /etc/sudoers`

выйти без сохранения: __Esc__ -> __shift + :__ -> __q!__

__выйти с сохранением: wq!__

![image](https://github.com/user-attachments/assets/cd59b18d-dbb2-4309-ac60-d8bc43d5ae2f)

---

### Запуск контейнеров в фоновом режиме:

`sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/9bb313f0-ed3d-4282-9b34-48c491eb8e55)

--- 

### Остановка контейнеров

останавливает все запущенные контейнеры, определённые в файле docker-compose.yml, но не удаляет их

`sudo docker compose stop`

![image](https://github.com/user-attachments/assets/737062df-5959-4c7f-856f-d1a15981c37a)

---

### Полное удаление контейнеров

полностью останавливает и удаляет все контейнеры, сети, объёмы данных (volumes) и другие ресурсы, созданные с помощью docker-compose.yml 

`sudo docker compose down`

![image](https://github.com/user-attachments/assets/3877db92-3d8c-4b3d-bb3d-49d89e669f4a)

---

### Проверка статуса контейнеров

показывает статус всех контейнеров, определённых в файле docker-compose.yml (команда выводит список контейнеров вместе с их состоянием (запущен/остановлен), портами, сетями и другими параметрами)

`sudo docker compose ps`

![image](https://github.com/user-attachments/assets/50afd43d-f3d1-4c04-afb6-686f2d4fd200)

---

### Клонирование удаленного Git-репозитория с GitHub

переход в нужную папку

`cd grafana_stack_for_docker` 



клонирование удаленного Git-репозитория с GitHub в папку:

`git clone https://github.com/vidmixx/OkorokovaVD.git`

![image](https://github.com/user-attachments/assets/b7498839-6aa0-4e44-8f59-657c12eab2d7)



копия файлов

`cp docker-compose.yaml docker-compose.yaml1`

![image](https://github.com/user-attachments/assets/9046f529-c83f-4e8e-952a-11d889e59866)



`cd /mnt/common_volume/swarm/grafana/config`

`cp prometheus.yaml  prometheus.yaml1`

![image](https://github.com/user-attachments/assets/1d0a5a19-5a99-470d-9a89-639703aff244)


`sudo docker-compose down`

![image](https://github.com/user-attachments/assets/10a66142-87fc-487e-8086-2c97eac692c7)

`sudo docker-compose stop`

![image](https://github.com/user-attachments/assets/21401011-d651-4868-b7e2-e7b7fea6e7d1)

ищем строчку -targets прописываем exporter:9100

![image](https://github.com/user-attachments/assets/bd9cec52-9489-46d6-be79-2e646f88c2d7)

`sudo docker-compose up -d`

![image](https://github.com/user-attachments/assets/0b857818-edfc-4e33-af25-7d07c1dcfc08)

localhost:3000 

User & Password GRAFANA: admin 

создание Dashboards: Home -> Connections -> Data sources -> Add data source

где нужно нажать на +Add visualization -> Configure a new data source -> Prometheus

настройки прометеуса: 

* http://prometheus:9090 
* Authentication: Basic authentication 

после того как все настроили нажимаем Save & test

создав Dashboards импортируем его: 

Home -> Dashboards -> Import dashboard

В поле нужно написать 1860 -> Load Select Prometheus -> Import -> Название Prometheus


![image](https://github.com/user-attachments/assets/c28bc724-80ec-44d3-8c1b-8f49b186ddd8)

