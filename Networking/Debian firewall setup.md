```
sudo apt install ufw gufw
sudo ufw enable
```
install and setup firewall.
```
gufw
```
run the firewall graphical user interface.
```
ufw status verbose
```
list the firewall status.
```
sudo ufw allow <protocol>|<port>
```
allow a protocol or port.
```
sudo ufw deny <protocol>|<port>
```
deny a protocol or port.
```
sudo ufw disable
```
disable the firewall.