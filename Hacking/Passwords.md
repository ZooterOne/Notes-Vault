## John the ripper

```
john --show=formats <password_file>
```

display possible formats for passwords.

```
john --wordlist=<wordlist> <password_file> [--format=<format>]
```

reverse hash passwords.

```
john --single <password_file> [--format=<format>]
```

reverse hash passwords using variations on usernames.

```
zip2john <zip_file> > <password_file>
rar2john <rar_file> > <password_file>
ssh2john <ssh_file> > <password_file>
```

extract hashed password from various files.

___

## Hashcat

```
hashcat <password_file> <wordlist>
```

reverse hash passwords using auto-detect mode.

```
hashcat -m <mode> <password_file> <wordlist>
```

reverse hash passwords using specific mode _(see help for list of modes)._

```
hashcat <command_options> --show
```

display the result of a previously run command.

_Alternatively results are in_ `~/.hashcat/hashcat.potfile`.

___

## Hydra

```
hydra -l <username> -P <wordlist> [-t <#tasks>] -vV <ip> <protocol>
```

reverse hash password for specific username.

_protocol:_ `ssh` | `sshkey` | `smb` | `ftp[s]` | `http[s]-{get|post}` | `http[s]-{get|post}-form`.

```
hydra -L <userlist> -P <wordlist> [-t <#tasks>] -vV <ip> <protocol>
```

reverse hash password for given usernames.

http\[s]-post-form examples:
- `https-post-form "<file.ext>:username=^USER^&password=^PASS^:F=Incorrect login"`.
- `https-post-form "<file.ext>:user=^USER^&pass=^PASS^:F=Bad login"`.
- `https-post-form "<file.ext>:<param>=<value>&login=^USER^&password=^PASS^:S=Success!!"`.