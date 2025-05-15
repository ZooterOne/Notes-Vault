## Update

```
flatpak update
```

update all Flatpak runtimes.

___

## Search

```
flatpak search <name> --columns=application
```

search for application id.

```
flatpak list
```

list installed runtimes.

___

## Install & remove

```
flatpak install <remote> <application id>
```

install an application.

```
flatpak uninstall <application id>
```

remove an application.

```
flatpak uninstall --unused --delete-data
```

remove all unused Flatpak runtimes.