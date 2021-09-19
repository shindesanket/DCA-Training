# Docker Swarm Services 

## Create and list the Services

```bash
docker service create --name=firstservice -p 80:80 httpd:alpine
```

Create a service multiple replicas

```bash
docker service create --name=secondservice --replicas=5 -p 80:80 nginx
```

List the services

```bash
docker service ls
```

List the tasks under the service

```bash
docker service ps firstservice
```

## Inspect the service to get more details 

```bash
docker service inspect firstservice
```

```bash
docker service inspect secondservice
```

## Service Logs 

```bash
docker service logs firstservice
```

```bash
docker service logs secondservice
```

## Delete the services 

```bash
docker service rm firstservice
```

```bash
docker service rm secondservice
```