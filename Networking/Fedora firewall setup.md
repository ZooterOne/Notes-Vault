```
firewall-cmd --list-all [--zone=<name>]
```

list information for the default/given zone.

```
firewall-cmd --list-services
```

list allowed services in current zone.

```
sudo firewall-cmd --add-service=ssh --timeout=15m
```

allow ssh service for 15 minutes.

```
firewall-cmd --list-ports
```

list allowed ports in the current zone.

```
sudo firewall-cmd --add-port=<number>/<type>
```

open a port for incoming traffic.

```
sudo firewall-cmd --remove-port=<number>/<type>
```

close a port for incoming traffic.

```
sudo firewall-cmd --runtime-to-permanent
```

make new settings persistent.

```
sudo firewall-cmd --reload
```

reload the settings.