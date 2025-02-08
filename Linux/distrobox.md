### Manage containers
```
distrobox-list
```
list containers.
```
podman ps -a
```
list podman containers.
```
distrobox-create --image <image> --name <name> [--home <path>]
```
create a container.
```
distrobox-create --clone <container> --name <name>
```
clone a container.
___
### Run containers
```
distrobox-enter <name>
```
enter container.
```
distrobox-stop --name <name>
```
stop a container.
```
distrobox-rm --name <name> [--force] [--rm-home]
```
delete a container.
```
distrobox-upgrade <name>
```
update a container.
```
distrobox-upgrade --all
```
update all containers.

`BoxBuddy` a graphical interface for Distrobox.