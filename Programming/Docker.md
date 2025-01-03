### Manage images
```
docker image ls
```
list stored image.
```
docker pull <image>[:<tag>]
```
download an image.
```
docker image rm <image>[:<tag>]
```
remove a stored image.
___
### Manage containers
```
docker ps
```
list running container.
```
docker ps -a
```
list all containers.
```
docker run [<options>] <image> [<command>] [<args>]
```
_options:_
- `-d`_: start the container in detach mode._
- `-it`_: run an interactive shell within the container._
- `-p <port>:<port>`_: expose a port._
- `--rm`_: remove the container when finished._
___
### Create image
```
docker build -t <name> .
```
build an image from Makerfile.
_Makerfile commands:_
- `FROM <image>`_: select base image._
- `RUN <command>`_: run a command._
- `WORKDIR <directory>`_: set the working directory._
- `COPY <file>`_: copy a file to the working directory._
- `EXPOSE <port>`_: expose a port._
- `CMD <command>`_: command to run when starting the container._