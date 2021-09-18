
# Docker storage and Volumes

To list all the current volumes

```bash
docker volume ls
```

To create a new volume

```bash
docker volume create testvol
```

Lets run a container mouting to this volume

```bash
docker run -itd --name=test -v testvol:/sanket centos:7
```

Check if volume is mounted correctly by going inside the container

```bash
docker exec -it test /bin/bash
```

```bash
docker volume ls
docker volume inspect testvol
```

Lets create some files in our container

```bash
docker exec -it test /bin/bash
cd sanket
echo "Hello" > abc.txt
echo "Welcome" > xyz.txt
```

Lets stop the container now

```bash
docker stop test
```

TO get the path of our volume 

```bash
docker volume inspect test
```

To see the fils on the volume 

```bash
ls -ltr /var/lib/docker/volumes/testvol/_data
```

Lets create new container and mount this volume to it

```bash
docker run -itd --name=testagain --mount source=testvol,destination=/sanket centos:7
```

```bash
docker exec -it testagain /bin/bash
```

Check for the files. Files should be present.

Remove the container and Volume 

```bash
docker rm test
docker rm testagain
docker volume rm testvol
```

Prune command to delete all volumes and get reclaimed space

```bash
docker volume prune
```
