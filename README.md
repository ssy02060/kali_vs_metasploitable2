# kali_vs_metasploitable2

### remove ALL CONTAINERS AND IMAGES
$ sudo docker rm -f $(sudo docker ps -aq)
$ sudo docker rmi $(sudo docker images -q)

### commit container
$ sudo docker commit -m "commit messages ~~~" [container-name (ex : kali)] [tag-name (ex : ssy02060/kali)]

### push image to registry
$ sudo docker login
input your Username and password

$ sudo docker push [tag-name (ex : ssy02060/kali)]

### create network to connect each containers
$ sudo docker network create --gateway 172.33.0.1 --subnet 172.33.0.0/16 broker

### run kali-linux with network:broker
$ sudo docker run -it --network=broker --name=kali ssy02060/kali

### run metasploitable with network:broker
$ sudo docker run -it --network=broker --name=metasploitable ssy02060/metasploitable