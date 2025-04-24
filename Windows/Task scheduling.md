## Command prompt

```
schtasks /query /tn <name> /fo list /v
```

display information about a task.

```
schtasks /create /tn <name> /sc ONLOGON /rl HIGHEST /tr "cmd /c <script>.bat"
```

schedule a script on logon.

```
schtasks /delete /tn <name>
```

delete a task.

___

## Powershell

```
$trigger = New-ScheduledTaskTrigger -AtStartup
$settings = New-ScheduledTaskSettingsSet -AllowStartIfOnBatteries -DisallowHardTerminate -StartWhenAvailable
$action = New-ScheduledTaskAction -Execute "cmd" -Argument "/c <script>.bat"
Register-ScheduledTask -TaskName <name> -User "NT AUTHORITY\SYSTEM" -Action $action -Settings $settings -Trigger $trigger -RunLevel Highest
```

schedule a script at startup.