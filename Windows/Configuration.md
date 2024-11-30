### Users
```
net user <username> <password> /add
```
setup a new user.
```
net localgroup administrators <username> /add
```
setup user as an administrator.
___
### File associations
```
assoc
```
get file associations.
```
assoc <filetype>=<program>
```
set file association.
___
### Firewall
```
netsh advfirewall set allprofiles state off
```
turn the firewall off.
```
netsh advfirewall set allprofiles state on
```
turn the firewall on.
___
### Hibernation
```
powercfg /hibernate off
```
turn hibernation off.