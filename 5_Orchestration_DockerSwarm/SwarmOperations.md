
# Swarm Operations

## Promote a node

```bash
sudo su
docker node promote <<worker node name>>
```

List the all nodes and observe worker node manager status 

```bash
docker node ls
```

## Demote a node

```bash
sudo su
docker node demote <<worker node name>>
```

List the all nodes and observe worker node manager status 

```bash
docker node ls
```

## Drain a node for performing upgrades and patches

```bash
docker node update --availability drain <<worker node name>>
```

List the all nodes and observe the availability column for worker node

```bash
docker node ls
```


## Activate back the drained node for making it available to schedule the workloads

```bash
docker node update --availability active <<worker node name>>
```

List the all nodes and observe the availability column for worker node

```bash
docker node ls
```

## Deleting the node from Swarm cluster

```bash
docker node update --availability drain <<worker node name>>
```

List the all nodes and observe the availability column for worker node

```bash
docker node ls
```

```bash
docker swarm leave
```