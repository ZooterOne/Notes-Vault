## Basics

```
ping -c <count> <ip>
```

send ICMP ECHO_REQUEST.

```
traceroute <ip>
```

trace packets route to ip.

```
nc -zv <ip> <port_range>
```

port scanning with netcat.

```
nc <ip> <port>
```

netcat as client.

___

## ARP Scan

```
nmap -PR -sn <ip_range>
```

ARP ping (_must be on the same network_).

___

## ICMP Scan

```
nmap -PE -sn <ip_range>
```

ICMP ping (echo).

```
nmap -PP -sn <ip_range>
```

ICMP ping (timestamp).

```
nmap -PM -sn <ip_range>
```

ICMP ping (address mask).

___

## TCP Scan

```
nmap -PS [<port_range>] -sn <ip_range>
```

TCP SYN ping.

```
nmap -PA [<port_range>] -sn <ip_range>
```

TCP ACK ping _(requires privileges)_.

```
nmap -sT <ip>
```

TCP connect scan.

```
nmap -sS <ip>
```

TCP SYN scan _(requires privileges)_.

```
nmap -sU <ip>
```

TCP UDP scan _(requires privileges)_.

```
nmap -sN <ip>
```

TCP NULL scan.

```
nmap -sF <ip>
```

TCP FIN scan.

```
nmap -sX <ip>
```

TCP Xmas scan.

```
nmap -sA <ip>
```

TCP ACK scan _(check firewall)_.

```
nmap -sW <ip>
```

TCP Window scan.

___

## Tips

Use decoys with `-D` option and fragment packets with `-f` or `-ff` _(see [[nmap]])_.