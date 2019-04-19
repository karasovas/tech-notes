# Docker swarm on Ubuntu 16.04
## Create docker Swarm cluster

```bash
# docker swarm init --advertise-addr  172.31.83.87
Swarm initialized: current node (jpzulo5kqrffje8go7wkuhz92) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-4aftzcmj99iagzujor02dg6ol00s6tuxmnrjyd0dcm083iibcn-70p6hj5qcy80u7cu4ndsh51b8 172.31.83.87:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

## Join node to docker swarm manager
```
docker swarm join --token SWMTKN-1-4aftzcmj99iagzujor02dg6ol00s6tuxmnrjyd0dcm083iibcn-70p6hj5qcy80u7cu4ndsh51b8 172.31.83.87:2377
```

## Launch web service in Docker Swarm
```
docker service create --name webserver -p 80:80 httpd
```

You can check running service using command below
```
docker service ls
ID                  NAME                MODE                REPLICAS            IMAGE               PORTS
kudjaj8rgggl        webserver           replicated          1/1                 httpd:latest        *:80->80/tcp
```

## Scale the service
```
docker service scale webserver=2
```

## Disconnect node from swarm
```bash
docker swarm leave
```
