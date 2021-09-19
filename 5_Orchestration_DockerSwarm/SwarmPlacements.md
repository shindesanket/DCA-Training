
# Docker Swarm Placement : Labels and Constraints

## Adding labels to the node

```bash
docker node update --label-add type=cpu-optimized <<name of worker 1>>
```

```bash
docker node update --label-add type=memory-optimized <<name of worker 2>>
```


## Scheduling service on specific nodes using constraints

```bash
docker service create --constraint=node.labels.type==cpu-optimized --name=nginx --replicas=3 nginx
```

```bash
docker service create --constraint=node.labels.type==memory-optimized --name=redis --replicas=3 redis
```

## Check if containers are created as per the labels and constraints


```bash
docker service ps nginx
docker service ps redis
```
