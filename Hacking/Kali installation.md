_select top10 only during installation._

```
apt install kali-linux-top10
```

install top10 from minimal installation (container `docker.io/kalilinux/kali-rolling:latest`).

List of packages: `https://www.kali.org/tools/kali-meta/`

```
apt update && apt full-upgrade -y
```

update system.

```
kali-tweaks
```

run system tweaks.

```
apt install dirb dirbuster gobuster hashcat whois wordlists
```

install basic packages.

```
apt install fern-wifi-cracker
apt install wifite
apt install steghide
apt install theharvester
apt install autopsy
apt install enum4linux
```

install optional packages.

```
apt install spice-vdagent
apt install spice-webdavd
```

enable directory share when using Boxes.

_shared drive is `dav://localhost:9843`._