## Update

```
dnf upgrade
```

update package database and all packages.

___

## Search

```
dnf search <name>
```

search for package.

```
dnf list --installed
```

list installed packages.

```
dnf list --upgrades
```

list packages with update available.

___

## Install & remove

```
dnf install <package>
```

install a package.

```
dnf remove <package>
```

remove a package.

```
dnf autoremove
```

remove all unused packages.

---

## Download

```
dnf download <package>
```

download a package without installation.

## Offline upgrade

```
dnf upgrade --offline
```

download the updated packages.

```
dnf offline reboot
```

reboot and upgrade packages.
