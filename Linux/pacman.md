## Update

```
pacman -Syu
```

update package database and all packages.

```
pacman -Syu --ignore=<package>
```

update packages ignoring a specific package.

```
pacman -Syu --ignoregroup=<package>
```

update packages ignoring a specific package group.

___

## Search

```
pacman -Ss <name>
```

search for package.

___

## Install & remove

```
pacman -S <package>
```

install a package.

```
pacman -R <package>
```

remove a package.

```
pacman -Rs <package>
```

remove a package and its dependencies.