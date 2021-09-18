
# Docker Networking Commands

To list all docker networks 

```bash
docker network ls
```

To Inspect the docker network

```bash
docker network inspect <<network id / name>>
```

Observe subnet and gatway sections in IPAM

Run a container "first" to verify default IP Address

```bash
docker run -itd  --name=first centos:7
```

Inspect the container to check network settings and IP address

```bash
docker inspect first
```

Run a container "second" to verify default IP Address

```bash
docker run -itd  --name=second centos:7
```

Inspect the container to check network settings and IP address

```bash
docker inspect second
```

To see current running containers

```bash
docker ps
```

Lets go inside first container and try to ping second container

```bash
docker exec -it first ping second
```

Lets go inside second container and try to ping second container

```bash
docker exec -it second ping first
```

Lets create custom network to make this DNS working.

To create a user defined custom network 

```bash
docker network create --driver=bridge --subnet=192.168.10.0/24 simplilearn
```

List the docker networks 

```bash
docker network ls
```

Lets inspect custom network "simplilearn"

```bash
docker network inspect simplilearn
```

Now lets create 2 containers with custom network and try to ping

```bash
docker run -itd --name=customfirst --net=simplilearn centos:7
docker run -itd --name=customsecond --net=simplilearn centos:7
docker exec -it customfirst ping customsecond
docker exec -it customsecond ping customfirst
```

To see the docker DNS 

```bash
docker exec -it customfirst cat /etc/resolv.conf
```

Check if first container can talk with customfirst container

```bash
docker exec -it first ping customfirst
```

Add first to custom network simplilearn and try pinging each other

```bash
docker network connect simplilearn first
docker exec -it first ping customfirst
docker inspect first
```

