```
net user <username> <password> /add
```

setup a new user.

```
net localgroup administrators <username> /add
```

setup user as an administrator.

```
net user <username>
```

display information about user.

```
net user <username> /time:M-F,7am-4pm
```

allow user access only at indicated times.

```
net user <username> /time:all
```

remove all time restrictions for user.

```
net user <username> /time:
```

remove user access.