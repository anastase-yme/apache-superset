# Установка Docker, Docker-compose, Apache Superset, Postgres, Pgadmin 

**1.** **Установка** **Docker, Docker-compose**

Если Docker и Docker-compose уже установлены, этот шаг пропускается. Проверить есть докер на сервере можно так:

`sudo systemctl status docker`

`docker-compose --version`

Если докера нет, для того чтобы иметь возможность запускать контейнеры на сервере нужно установить его, выполнив следующие команды:

`sudo apt update`

`sudo apt install apt-transport-https ca-certificates curl software-properties-common`

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add –`

`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"`

`sudo apt update`

`apt-cache policy docker-ce`

`sudo  apt  install  docker-ce`

Чтобы использовать утилиту docker, нужно добавить ваше имя пользователя в группу Docker. Для этого в терминале вводятся команды:

`sudo  usermod -aG  docker ${user}`

`su - ${user}`

Проверка работоспособности докера:

`docker run hello-world`

После  этого  переходим  к  установке Docker Compose:

`sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

`sudo chmod +x /usr/local/bin/docker-compose`

Проверить успех установки можно так:

`sudo systemctl status docker`

`docker-compose –version`

**2.** **Установка Apache Superset, Postgres, Pgadmin**

Понадобиться определённая структура расположения файлов:

    ├───superset

       ├───dockerfile

       ├───superset_config.py

       └───superset-init.sh

    └───docker-compose.yml

Удобнее всего создать данные файлы и директории в отдельной директории в /home.

В файле docker-compose.yml указываются логины и пароли.

Далее необходимо перейти в директорию /home/apache-superset и выполнить команды:

`docker-compose build`

`docker-compose up -d`

**___________________________________________________________**

Проверить, что контейнеры успешно работают, можно так:

`docker  ps`

Посмотреть логи контейнеров:

`docker logs <container_id>`

Остановить и удалить все существующие контейнеры:

`docker-compose down`

Удалить вольюмы:

`docker volume rm  <имя>`
