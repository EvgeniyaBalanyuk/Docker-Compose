# Docker-Compose

## Task 1
[Ссылка на Docker Hub](https://hub.docker.com/repository/docker/evgeniyabal/custom-nginx/general)

## Task 2

![](https://github.com/EvgeniyaBalanyuk/Docker-Compose/blob/main/Task2.png)

## Task 3

![](Task3.1.png)

Контейнер будет в состоянии "Exited". Это произошло потому, что при нажатии Ctrl-C, прерывается основное приложение (Nginx), которое работает внутри контейнера, и контейнер завершил свою работу, так как в Docker контейнеры работают до тех пор, пока основное приложение не завершится.

![](Task3.2.png)

Проблема, скорее всего, в том, что Nginx теперь слушает на порту 81, а docker port custom-nginx-t2 может быть настроен на проброс порта 80 к 8080 на хосте, что означает, что запросы на http://127.0.0.1:8080 не перенаправляются на новый порт 81 внутри контейнера.
Порт 8080 на хосте по-прежнему пробрасывается к порту 80 внутри контейнера, но Nginx больше не слушает на порту 80.

![](Task3.3.png)

## Task 4

![](Task4.png)

## Task 5

![](Task5.1.png)

Docker по умолчанию ищет файл с именем docker-compose.yaml. В данном случае, файл docker-compose.yaml будет использоваться, потому что именно это имя Docker рассматривает как дефолтное. Файл compose.yaml будет проигнорирован.

![](Task5.2.png)

![](Task5.3.png)

![](Task5.4.png)

Сообщение Found orphan containers ([task5-portainer-1]) for this project говорит о том, что в системе остались контейнеры, которые не соответствуют текущему определению стека. Контейнер task5-portainer-1, который был запущен из файла compose.yaml, который был удален.
