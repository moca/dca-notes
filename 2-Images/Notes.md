# Docker Images

- A docker image is a file containing the code and compontnents needed to run sw in a container.
- Images (and containers) use a layered file system. Each layer containe only deltas from previous image.
- The image consists of one or more read only, while a container adds a writable layer.

The advantage of a layered FS resides on the sharing of layers between images, this results in :
- smaller storage footprint
- faster image transfer
- faster image build

## Dockerfiles

Dockerfile is a set of instruction which are used to construct a Docker image. These instruction are called **directives**.

Some common directives :
- **FROM** Start a new build stage and sets the base image. Must be the first directive (except ARG)
- **ENV** Set environment variables useful at runtime
- **RUN** Created a new layer, by running a cmd and commiting changes
- **CMD** Specifies a default command when running a container.
- **EXPOSE** Documents which port are intended to be published when running a container.
- **WORKDIR** sets the directory where other directives **ADD**, **COPY**, **CMD**, **ENTRYPOINT** will apply. They can be absolute or relative (to previous)
-  **COPY** copy files from local host to container. 
-  **ADD** like **COPY** but can also pull from URL, and extract a compressed archive. However, only COPY can be used to select data from a multi-stage build.
-  **STOPSIGNAL** specify the signal that will be send to the container on stop.
-  **HEALTHCHECK** Specify a command to do health checl

See more https://docs.docker.com/engine/reference/builder/

## Building image 

Use the command `docker build -t TAG .` to run the image `docker run IMAGE`.

## Efficient docker images

- Smaller images are more easy to start/stop/delete
- Put things less likely to change on lower-level layers
- Dont create unnecessary layers
- **Avoid including unnecessary files and packages** --> take advantage of multi-stage builds.


### Multi-stage builds

- Multi-stage builds have more than one FROM directive. 
- Each stage begins a completely new FS layering.
  + Allowing to selectively copy only the files needed from previous layers

Two options to copy from a previous stage :
- Unnamed stage, use the stage number  (zero indexed): `COPY --from=0`
- Named stade `FROM <image> AS stage1` : `COPY --from=stage1`

## Managing Images

- `docker [image] pull IMAGE[:TAG]` download an  image
- `docker image ls` list images
- `docker image ls -a` include intermediate images
- `docker [image] inspect IMAGE` get detail info about an image
- `docker [image] inspect IMAGE --format TEMPLATE` to get only a subset of information
- `docker [image] rm IMAGE[:tag]` or `docker rmi IMAGE[:tag]` to delete an image add `-f` to remove tags and delete the image, might create dnagling image in the host.
- `docker image prune` delete unused images from the system
## Flattening image

Sometimes we want to flatten the layers. There is no official method to do so, however there is a simple workaround :
- run a container from the image
- export container
- import container

**Export/import process flattens the image to one single layer !**


## Docker Registries

A registry is responsible for storing and distributing Docker images.

- By default we use _Docker HUB_
- Two other options for creating your own registry (with Docker)
  + Use OSS Docker Registry
  + Enterprise Solution _Docker Trusted Registry_


To create a basic registry, simply run the registry image and publish port 5000.

`docker run -d -p 5000:5000 --restart=always --name registry -e REGISTRY_LOG_LEVEL=debug registry:2` 



