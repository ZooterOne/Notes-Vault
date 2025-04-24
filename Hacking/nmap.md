## Scan ports

```
nmap <ip> [options]
```

Options:
- `-p <port_range>`_: only provided ports._
- `-p-`_: all ports._
- `-sT|U|X`_: TCP|UDP|Xmas scan._
- `-sS`_: SYN/Stealth scan._
- `-sV`_: detect version of the sources._
- `-O`_: detect Operating System._
- `-Pn`_: skip host discovery._
- `-f`_: fragment the packets into 8 byte-fragments._
- `-ff`_: fragment the packets into 16 byte-fragments._
- `-D RND:<#>`_: generate random decoy addresses._

___

## Ping scan

```
nmap -sn <ip_range> [options]
```

Options:
- `-A`_: run OS & version detection and scripts._
- `-sC`_: run default scripts._
- `--script=<script>`_: run a script. Scripts are located in `/usr/share/nmap/scripts`._
- `--script-args <script>.<args>=<value>`_: script arguments._
- `-T<0-5>`_: timing template (0=paranoid|5=insane)._
- `-v`_: verbosity level 1._
- `-vv`_: verbosity level 2._
- `-oA <base_name>`_: output 3 major formats._
- `-oG <file.gmap>`_: output grep-able format._