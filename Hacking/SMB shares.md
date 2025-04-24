```
enum4linux -a <ip>
```

display SMB shares.

```
smbclient //<ip>/<share> [-U <username>[%<password>]] [-p <port>]
```

access SMB share.

```
nmap -p <port> --script=smb-enum-shares.nse,smb-enum-users.nse <ip>
```

display SMB shares and users.

```
smbget -R smb://<ip>/<share>
```

recursively copy the content of the share.