## Update

```
apt update
```

update package database.

```
apt upgrade
```

update all packages.

```
sudo apt update && sudo apt full-upgrade -y
```

full system update.

___

## Search

```
apt search <name>
```

search for package.

```
apt list --installed
```

list installed packages.

```
apt list --upgradable
```

list packages with update available.

___

## Install & remove

```
apt install <package>
```

install a package.

```
apt install <file.deb>
```

install a package from a file.

```
apt remove <package>
```

remove a package.

```
apt purge <package>
```

remove a package and all related files/data.

```
apt autoremove
```

remove all unused packages.