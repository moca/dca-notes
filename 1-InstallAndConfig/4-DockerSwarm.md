# Docker Swarm

Swarm provides many useful features, and can help on orchestration, HA, and scaling.

To start your swarm cluster you will need a master and some nodes.


## Create a Swarm Cluster
To launch a master, use the command :

`docker swarm init --advertise-addr IP_ADDR`

To join a worker to the cluster :
- On master execute the `docker swarm join-token worker` this will provide the right command to execute on worker node.
- On worker node, the command will look like : `docker swarm join --token SWMTKN-TOKEN MASTER_NODE_IP:2377`
- To verify addition we can use `docker nodes ls`

## Backup a swarm cluster

To backup :
- stop docker service
- `sudo tar -zvcf backupt.tar.gz /var/lib/docker/swarm`
- start the docker service

## Restore cluster
To restore from backup:
-  stop docker service : `sudo systemctl stop docker`
-  delete any existing files or directories under :  `sudo rm -rf /var/lib/docker/swarm/*`
- copy backed-up files : `sudo tar -zxvf backup.tar.gz -C /var/lib/docker/swarm/`
- restart docker service : `sudo systemctl start docker`

