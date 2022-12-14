## Основные команды Docker ##

***docker version*** - версии Docker клиента и сервера

***docker ps*** - список запущенных **Containers**

***docker ps -a*** - список запущенных и остановленных **Containers**

***docker images*** - список локальных **Images**

## Работа с контейнерами

### Создание контейнеров

***docker run image_name*** - создание и запуск контейнера. Сначала образ ищётся локально, затем в DockerHub

***docker run -it image_name*** - interactive terminal - подключение к процессу внутри контейнера

***docker run -d image_name*** - запуск контейнера в фоновом режиме

***docker run --rm image_name*** - автоматическое удаление контейнера после остановки

***docker run --name my_container_name image_name*** - присвоение произвольного имени запускаемому контейнеру

***/*** - разбиение команды на несколько строк

***docker run -d -e MY_ENV_VARIABLE=test nginx*** - присвоение значения переменной среды


### Остановка и удаление контейнеров

***docker stop container_id/container_name*** - остановка контейнера

***docker kill container_id/container_name*** - моментальная остановка контейнера, если stop не работает

***docker rm container_id/container_name*** - удаление остановленного контейнера

***docker container prune*** - удаление всех остановленных контейнеров

***docker container inspect container_id/container_name*** - детали выбранного контейнера

## Команды процессам в контейнере ##

***hostname*** - совпадает с id контейнера

***hostname -i*** - ip

***docker exec -it container_id/container_name bash*** - запуск процесса внутри запущенного контейнера

***docker run -p 8080:80 nginx - публикация порта. Docker перебросит внешний порт 8080 на внутренний порт 80 в контейнер

***docker run -v ${PWD}:/usr/share/nginx/html nginx - публикация тома. PWD - переменная, путь к текущей локальной папке

## Создание образа ##

***docker build .*** - создание образа, если dockerfile находится в текущей директории

***docker build . -f*** - если имя Dockerfile отличается от "Dockerfile"

***docker build . -t my_colendar:1.0.0*** - добавляение названия и тэга

## Docker-compose ##

***docker-compose up*** - создается сеть, образы (если не созданы) и разворачивются контейнеры внутри этой сети, 
согласно yaml-файла

***docker-compose down*** - остановить и удалить все контейнеры

***docker volume ls*** - показать тома, подключенные на Docker Host
