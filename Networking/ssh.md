### Login
```
ssh <username>@<ip>
```
remote login using ssh.
```
ssh -i <file> <username>@<ip>
```
remote login using a key file _(usually id_rsa)_.
___
### Copy files
```
scp <username>@<ip>:<file> <file>
```
copy remote file locally.
```
scp <file> <username>@<ip>:<file>
```
copy local file to remote system.