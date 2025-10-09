# Manage containers

```
distrobox list
```

list containers.

```
podman ps -a
```

list podman containers.

```
distrobox create --compatibility
```

show list of compatible images.

```
distrobox create --image <image> --name <name> [--hostname <hostname>]
```

create a container.

```
distrobox create --image <image> --name <name> --home <path>
```

create a container using a specific home folder.

```
distrobox create --image <image> --name <name> --nvidia
```

create a GPU enabled container.

```
distrobox create --image <image> --name <name> --unshare-netns
```

create a container with host IP not shared with the container.

```
distrobox create --image <image> --name <name> --unshare-all
```

create an isolated container with limited sharing from host.

```
distrobox create --image <image> --name <name> --unshare-all --init
```

create a more isolated container using its own init system.

```
distrobox create --clone <container> --name <name>
```

clone a container.

```
distrobox rm <name>
```

delete a container.

```
distrobox rm <name> --force
```

force deletion of a container.

```
distrobox rm <name> --rm-home
```

delete a container including the specific home folder.

```
distrobox upgrade <name>
```

update a container.

```
distrobox upgrade --all
```

update all containers.

___

# Run containers

```
distrobox enter <name>
```

enter a container.

```
DBX_CONTAINER_MANAGER="<manager>" distrobox enter <name>
```

enter a container with specific manager (_docker_ or _podman_).

```
distrobox enter <name> -- <command>
```

enter a container and immediately execute a command.

```
distrobox stop <name>
```

stop a container.

```
distrobox stop --all
```

stop all containers.

---

# Commands inside the container

```
distrobox-host-exec <command>
```

execute a command on the host.

```
distrobox-export --app <name>
```

export an application to the host.

```
distrobox-export --app <name> --delete
```

un-export an application from the host.

---

# Tips

`BoxBuddy` a graphical interface for Distrobox.

Run `chsh -s /bin/<shell>` inside the container to change the default shell.