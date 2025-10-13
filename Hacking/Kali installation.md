# Regular installation

_select top10 only during installation._

```
sudo apt install kali-tools-top10
```

install top10 from minimal installation.

```
sudo apt update && apt full-upgrade -y
```

update system.

# Distrobox installation

```
distrobox create --name Kali --image docker.io/kalilinux/kali-rolling:latest --home <path> --hostname Kali --init-hooks "sudo apt install kali-system-cli kali-linux-core kali-tools-top10 kali-tweaks -y" --unshare-all --init --additional-flags "--network=bridge"
```

create an isolated Kali box and install minimal tools.

```
distrobox enter Kali
```

enter the Kali box.

# Common

List of packages: `https://www.kali.org/tools/kali-meta/`

```
kali-tweaks
```

run system tweaks.

```
sudo apt install dirb dirbuster gobuster hashcat whois wordlists
```

install basic packages.

```
sudo apt install fern-wifi-cracker
sudo apt install wifite
sudo apt install steghide
sudo apt install theharvester
sudo apt install autopsy
sudo apt install enum4linux
```

install optional packages.

# Boxes

```
sudo apt install spice-vdagent
sudo apt install spice-webdavd
```

enable directory share when using Boxes.

_shared drive is `dav://localhost:9843`._