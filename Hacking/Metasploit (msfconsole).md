### Basics
```
msfconsole
```
run metasploit console.
___
### Modules
```
search <string>
```
search module/exploit/payload.
```
use <module>
```
use specific module.
```
show payloads
```
display all payloads.
```
set payload <number>
```
set active payload.
___
### Options
```
show options
```
display active module options.
```
set <parameter> <value>
```
set active module parameter.
```
setg <parameter> <value>
```
set global parameter.
```
unset <parameter>
```
unset parameter.
```
unset all
```
unset all parameters.
___
### Run
```
run
```
run active module.
```
back
```
exit active module.
___
### Sessions
```
sessions
```
display all sessions.
```
sessions -i <id>
```
interact with specific session.
___
### Reverse shell
```
use exploit/multi/handler
set PAYLOAD <payload>
set LHOST <ip>
set LPORT <port>
run
```
catch reverse shell.
___
### Meterpreter
```
upload <file>
```
upload a local file.
```
load powershell
```
load Powershell.
```
powershell_shell
```
enter Powershell.
```
shell
```
run a command line shell.