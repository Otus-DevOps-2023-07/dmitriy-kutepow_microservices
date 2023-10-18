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
