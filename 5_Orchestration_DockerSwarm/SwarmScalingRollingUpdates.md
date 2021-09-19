# Swarm Scaling, Rolling Updates and Rollbacks


## Scale Up and Scale Down the Service

```bash
docker service create --name=firstservice -p 80:80 httpd:alpine
```

Scale Up

```bash
docker service update --replicas=5 firstservice
docker service ls
docker service ps firstservice
```

Scale Down


```bash
docker service update --replicas=1 firstservice
docker service ls
docker service ps firstservice
```

## Rolling Updates 

```bash
docker service update --replicas=5 firstservice
docker service update --image=httpd:2 firstservice
```

```bash
docker service update --update-delay 5s --image=httpd:alpine
```

```bash
docker service update --replicas=15 firstservice
docker service update --update-parallelism 3 --image=httpd:2 firstservice
```

## Rollback

```bash
docker service update --rollback firstservice
```






