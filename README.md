## ДЗ №18 Применение системы логирования в инфраструктуре на основе Docker
Что сделано:
```
1.Подготовил окружения
2.Логирование Docker-контейнеров
3.Сбор неструктурированных логов
4.Визуализация логов
5.Сбор структурированных логов
6.Распределенный трейсинг
```
Command list:
```
 1560  printenv USER_NAME
 1561  export USER_NAME='dimkutep'
 1562  printenv USER_NAME
 1563  sudo docker login -u ********* -p **********
 1564  cd ./docker/ui && bash docker_build.sh && docker push $USER_NAME/ui
 1565  cd ../post-py && bash docker_build.sh && docker push $USER_NAME/post
 1566  cd ../comment && bash docker_build.sh && docker push $USER_NAME/comment
 1567  sudo add-apt-repository ppa:longsleep/golang-backports
 1568  sudo apt update
 1569  sudo apt install golang-go
 1570  cd .
 1571  cd ..
 1572  cd logging/fluentd
 1573  cd ..
 1574  cd logging/fluentd
 1575  sudo docker build -t $USER_NAME/fluentd .
 1576  cd docker && docker-compose up -d
 1577  cd ..
 1578  cd docker && sudo docker-compose up -d
 1579  sudo docker-compose logs -f post
 1580  sudo docker ps -a
 1581  sudo docker-compose logs -f post
 1582  ршыещкн
 1583  history
 1584  cd ./docker/ui && bash docker_build.sh && docker push $USER_NAME/ui
 1585  cd ui && bash docker_build.sh && docker push $USER_NAME/ui
 1586  cd ../post-py && bash docker_build.sh && docker push $USER_NAME/post
 1587  cd ../comment && bash docker_build.sh && docker push $USER_NAME/comment
 1588  history
  1589  sudo docker ps -a
 1590  cd ..
 1591  sudo docker-compose -f docker-compose-logging.yml up -d
 1592  sudo docker-compose down
 1593  sudo docker-compose up -d
 1594  export USER_NAME=dimkutep
 1595  sudo docker-compose down
 1596  sudo docker login -u ******* -p *****
 1597  sudo docker-compose down
 1598  sudo docker-compose up -d
 1599  sudo docker-compose -f docker-compose-logging.yml up -d
 1600  sudo docker-compose down
 1601  sudo docker-compose up -d
 1602  cd ..
 1603  cd logging/
 1604  cd fluentd/
 1605  sudo docker build -t dimkutep/fluentd .
 1606  cd ..
 1607  cd docker/
 1608  sudo docker-compose -f docker-compose-logging.yml up -d fluentd
 1609  sudo docker-compose up -d
 1610  sudo docker ps -a
 1611  sudo docker-compose stop ui
 1612  sudo docker-compose rm ui
 1613  sudo docker-compose up -d
 1614  cd ..
 1615  cd logging/fluentd/
 1616  sudo docker build -t dimkutep/fluentd .
 1617  cd ..
 1618  cd docker/
 1619  sudo docker-compose -f docker-compose-logging.yml up -d fluentd
 1620  cd logging/fluentd/
 1621  cd ..
 1622  cd logging/fluentd/
 1623  sudo docker build -t dimkutep/fluentd .
 1624  cd ..
 1625  cd docker/
 1626  sudo docker-compose -f docker-compose-logging.yml up -d fluentd
 1627  sudo docker ps -a
 1628  sudo docker-compose up -d
 1629  history
 1630  sudo docker-compose -f docker-compose-logging.yml up -d fluentd
 1631  sudo docker ps -a
 1632  cd ..
 1633  cd logging/fluentd/
 1634  sudo docker build -t dimkutep/fluentd .
 1635  cd ..
 1636  cd docker/
 1637  sudo docker-compose -f docker-compose-logging.yml up -d fluentd
 1638  sudo docker ps -a
 1639  sudo docker logs 24c50315386c
 1640  sudo docker-compose -f docker-compose-logging.yml -f docker-compose.yml down
 1641  sudo docker-compose -f docker-compose-logging.yml -f docker-compose.yml up -d
 1642  history
```

## ДЗ №17 Введение в мониторинг. Модели и принципы работы систем мониторинга
Ссылка на докерхаб https://hub.docker.com/repositories/dimkutep
Что сделано:
```
1.Сконфигурировал, запустил и ознакомился с Prometheus
2.Настроил мониторинг состояния микросервисов
3.Сбрал метрики хоста с использованием node экспортера
```
Command list:
```
 1405  export USER_NAME=dimkutep
 1409  sudo docker login -u **** -p ******
 1410  sudo docker build -t $USER_NAME/prometheus .
 1411  cd ..
 1417  for i in ui post-py comment; do cd src/$i; bash docker_build.sh; cd -; done
 1418  cd docker/
 1419  sudo docker-compose up -d
 1420  sudo docker ps -a
 1421  sudo docker push
 1422  sudo docker images
 1423  sudo docker push dimkutep/ui
 1424  sudo docker-compose up -d
 1430  sudo docker-compose stop post
 1431  sudo docker-compose start post
 1436  sudo docker build -t $USER_NAME/prometheus .
 1440  sudo docker-compose up -d
 1442  sudo docker login
 1443  sudo docker push $USER_NAME/ui
 1444  sudo docker push $USER_NAME/commit
 1445  sudo docker push $USER_NAME/comment
 1446  sudo docker push $USER_NAME/post\
 1447  sudo docker push $USER_NAME/post
 1448  sudo docker push $USER_NAME/prometheus
 1449  sudo docker-compose down

```

## ДЗ №16 Устройство Gitlab CI. Построение процесса непрерывной интеграции
Что сделано:
```
1.Подготовлена инсталляцию Gitlab CI
2.Подготовлен репозиторий с кодом приложения
3.Описаны для приложения этапы пайплайна
4.Определены окружения
5.Настроено динамическое окружение
```
Command list:
```
docker_install.sh
#!/bin/bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update


    1  sudo vi docker_install.sh
    2  sh docker_install.sh
    3  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    4  sudo docker run hello-world
    8  mkdir -p /srv/gitlab/config /srv/gitlab/data /srv/gitlab/logs
    9  sudo mkdir -p /srv/gitlab/config /srv/gitlab/data /srv/gitlab/logs
   10  cd /srv/gitlab
   11  touch docker-compose.yml
   12  sudo vi docker-compose.yml
   15  apt install docker-compose
   16  sudo apt install docker-compose
   14  docker-compose up -d
   74  sudo docker exec 8fa5dcac4e94 cat /etc/gitlab/initial_root_password
   75  ls -la
   76  cd ..
   77  cd srv/gitlab/
   78  sudo vi docker-compose.yml
   79  sudo docker-compose up -d
   83  sudo docker run -d --name gitlab-runner --restart always -v /srv/gitlab-runner/config:/etc/gitlab-runner -v /var/run/docker.sock:/var/run/docker.sock gitlab/gitlab-runner:latest
   84  sudo docker exec -it gitlab-runner gitlab-runner register --url http://158.160.100.126/ --non-interactive --locked=false --name DockerRunner --executor docker --docker-image alpine:latest --registration-token GR1348941sZz9xNGVRYg2Yats8ynu --tag-list "linux,xenial,ubuntu,docker" --run-untagged


```

## ДЗ №15 Сетевое взаимодействие Docker контейнеров. Docker Compose. Тестирование образов
Что сделано:
```
1.Разобрался с работой сетей в Docker: none, host, bridge.
2.Установил docker-compose на локальную машину
3.Собрал образы приложения reddit с помощью docker-compose
4.Запустил приложение reddit с помощью docker-compose
```
Command list:
```
docker run -ti --rm --network none joffotron/docker-net-tools -c ifconfig
docker run -ti --rm --network host joffotron/docker-net-tools -c ifconfig
docker network create reddit --driver bridge
docker run -d --network=reddit --network-alias=post_db --network-
alias=comment_db mongo:latest
docker run -d --network=reddit --network-alias=post <your-login>/post:1.0
docker run -d --network=reddit --network-alias=comment <your-login>/comment:1.0
docker run -d --network=reddit -p 9292:9292 <your-login>/ui:1.0
docker network create back_net --subnet=10.0.2.0/24
docker network create front_net --subnet=10.0.1.0/24
docker run -d --network=front_net -p 9292:9292 --name ui <your-login>/ui:1.0
docker run -d --network=back_net --name comment <your-login>/comment:1.0
docker run -d --network=back_net --name post <your-login>/post:1.0
docker run -d --network=back_net --name mongo_db --network-alias=post_db --network-alias=comment_db mongo:latest
docker network connect front_net post
docker network connect front_net comment
```

## ДЗ №13 Docker контейнеры. Docker под капотом
Что сделано:
```
1.Установил Docker, Docker-compose, Docker-machine.
2.Успешно проверил работу докер с помошью docker run hello-world
3.Инициализировал консоль яндекс клауд yc init
4.Создал докер-хост
5.Инициализировал окружение докер на докер-хост
6.Написал Докерфайл и конфиги
7.Собрал образ
8.Запустил контейнер
9.Зарегистрировался в докер-хаб
10.Запушил получившийся образ в докер-хаб
11.Проверил работоспособность на локальной машине.
```
Command list:
```
 1111  cd dmitriy-kutepow_microservices/
 1112  git branch
 1113  history
 1114  git branch docker-2
 1115  git branch
 1116  git checkot docker-2
 1117  git checkout docker-2
 1118  cd /.ssh/
 1119  cd ~/.ssh/
 1120  ls la
 1121  ls -la
 1122  cd ..
 1123  cd dmitriy-kutepow_microservices/
 1124  yc compute instance create   --name docker-host   --zone ru-central1-a   --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4   --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15   --ssh-key ~/.ssh/ubuntu.pub
 1125  yc compute instance create   --name docker-host   --zone ru-central1-a   --network-interface subnet-name=ru-central1-a,nat-ip-version=ipv4   --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15   --ssh-key ~/.ssh/ubuntu.pub
 1126  yc init
 1127  yc compute instance create   --name docker-host   --zone ru-central1-a   --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4   --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15   --ssh-key ~/.ssh/ubuntu.pub
 1128  docker-machine create   --driver generic   --generic-ip-address=158.160.114.80   --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1129  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.114.80   --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1130  docker-machine -v
 1131  sudo docker-machine -v
 1132  curl -L https://github.com/docker/machine/releases/download/v0.16.1/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine && chmod +x /tmp/docker-machine && sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
 1133  sudo docker-machine -v
 1134  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.114.80   --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1135  sudo docker-machine create   --driver generic   --generic-ip-address=10.128.0.29  --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1136  sudo docker-machine ls
 1137  sudo docker-machine rm docker-host
 1138  sudo docker-machine create   --driver generic   --generic-ip-address=10.128.0.29  --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1139  sudo docker-machine ls
 1140  sudo docker-machine rm docker-host
 1141  sudo docker-machine ls
 1142  yc compute instance create   --name docker-host   --zone ru-central1-a   --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4   --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15   --ssh-key ~/.ssh/ubuntu.pub
 1143  sudo docker-machine create   --driver generic   --generic-ip-address=10.128.0.12  --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1144  sudo docker-machine ls
 1145  sudo docker-machine rm docker-host
 1146  sudo docker-machine create   --driver generic   --generic-ip-address=10.128.0.12  --generic-ssh-user dima   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1147  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.40.159  --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1148  sudo docker-machine rm docker-host
 1149  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.40.159  --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1150  sudo docker-machine ls
 1151  sudo docker-machine rm docker-host
 1152  yc compute instance create   --name docker-host   --zone ru-central1-a   --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4   --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15   --ssh-key ~/.ssh/ubuntu.pub
 1153  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.108.121  --generic-ssh-user ubuntu   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1154  sudo docker-machine ls
 1155  sudo docker-machine rm docker-host
 1156  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.108.121  --generic-ssh-user dima   --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1157  sudo docker-machine ls
 1158  sudo docker-machine rm docker-host
 1159  yc compute instance create   --name docker-host   --zone ru-central1-a   --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4   --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15   --ssh-key ~/.ssh/appuser.pub
 1160  sudo docker-machine ls
 1161  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.108.121  --generic-ssh-user appuser   --generic-ssh-key ~/.ssh/appuser   docker-host
 1162  sudo docker-machine ls
 1163  sudo docker-machine rm docker-host
 1164  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.114.208  --generic-ssh-user appuser   --generic-ssh-key ~/.ssh/appuser   docker-host
 1165  sudo docker-machine ls
 1166  sudo docker-machine rm docker-host
 1167  yc compute instance create   --name docker-host   --zone ru-central1-a   --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4   --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1804-lts,size=15   --ssh-key ~/.ssh/ubuntu.pub
 1168  sudo docker-machine ls
 1169  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.114.208  --generic-ssh-user yc-user  --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1170  sudo docker-machine ls
 1171  sudo docker-machine rm docker-host
 1172  sudo docker-machine create   --driver generic   --generic-ip-address=158.160.118.250 --generic-ssh-user yc-user  --generic-ssh-key ~/.ssh/ubuntu   docker-host
 1173  sudo docker-machine ls
 1174  eval $(docker-machine env docker-host)
 1175  eval $(sudo docker-machine env docker-host)
 1176  sudo docker run --rm -ti tehbilly/htop
 1177  sudo docker run --rm --pid host -ti tehbilly/htop
 1178  cd docker-monolith/
 1179  sudo docker build -t reddit:latest .
 1180  sudo docker images -a
 1181  sudo docker run --name reddit -d --network=host reddit:latest
 1182  sudo docker-machine ls
 1183  sudo docker login
 1184  sudo docker tag reddit:latest dimkutep/otus-reddit:1.0
 1185  sudo docker push dimkutep/otus-reddit:1.0
 1186  sudo docker logs reddit -f
 1187  sudo docker exec -it reddit bash
 1188  sudo docker inspect /otus-reddit:1.0
 1189  sudo docker inspect otus-reddit:1.0
 1190  sudo docker images -a
 1191  sudo docker inspect dimkutep/otus-reddit:1.0
 1192  sudo docker-machine rm docker-host
 1193  sudo yc compute instance delete docker-host
 1194  yc compute instance delete docker-host
```
