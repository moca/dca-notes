# Running a container

We run container using the docker run command ...

> `docker run [options] IMAGE[:TAG] [COMMAND] [ARG...]`

- IMAGE - the container image, by default from docker hub registry
- TAG - A specific image tag. Usually a specific version
- CMD - A command to run inside the container
- ARG - Argument to pass running the command 

Commonly used options :

- `-d` > detached mode, docker run cmd will exit and the container run in the background.
- `--name` > to give a more descriptive name to the container
- `--restart` > When to restart the container :
    + no > by default
    + on-failure > non zero exit code
    + always > start whatever situation. Starts the container on daemon startup.
    + unless-stopped > same as always but dont restart if manually stopped.
- `-p <host port>:<container port>` exposes a container port by mapping it to a port on host. You can map multiple ports at the same time.
- `--rm` deletes the container after execution
- `--memory` limits memory usage
- `--memory-reservation` soft limit on memory usage. Container will be restricted to this limit if Dockkr detects server runs out of memory.


## Managing the containers

- `docker ps` list all the running containers
  - use `-a` flag to list all containters, including exited ones
- `docker container stop/start` to stop/start  container
- `docker container rm` to delete a stopped container


