# Docker Images

- A docker image is a file containing the code and compontnents needed to run sw in a container.
- Images (and containers) use a layered file system. Each layer containe only deltas from previous image.
- The image consists of one or more read only, while a container adds a writable layer.

The advantage of a layered FS resides on the sharing of layers between images, this results in :
- smaller storage footprint
- faster image transfer
- faster image build

# Dockerfiles

Dockerfile is a set of instruction which are used to construct a Docker image. These instruction are called **directives**.

Some common directives :
- **FROM** Start a new build stage and sets the base image. Must be the first directive (except ARG)
- **ENV** Set environment variables useful at runtime
- **RUN** Created a new layer, by running a cmd and commiting changes
- **CMD** Specifies a default command when running a container.
- **EXPOSE** Documents which port are intended to be published when running a container.

For more directives see : https://docs.docker.com/engine/reference/builder/

# Building image 

Use the command `docker build -t TAG .` to run the image `docker run IMAGE`.


