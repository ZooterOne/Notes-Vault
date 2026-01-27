## Enumerate urls

```
ffuf -u http://<domain>/FUZZ -w <wordlist>
```

Enumerate urls.

```
ffuf -u http://<domain>/FUZZ -w <wordlist> -e .php,.html,.txt
```

Enumerate _(public)_ files.

```
ffuf -u http://FUZZ.<domain> -w <wordlist>
```

___

## Enumerate usernames

```
ffuf -w <wordlist> -X POST -d <data> -H "Content-Type: application/x-www-form-urlencoded" -u <url> -mr <message>
```

enumerate valid usernames from sign-up/password reset page.

_data: fields to fill-up, like_ `"username=FUZZ&&password=x"` _or_ `"username=FUZZ&&email=x"`.

_message: validation message, like_ `"username already exists"`.

___

## Brute force users & passwords

```
ffuf -w <userlist>:W1,<wordlist>:W2 -X POST -d <data> -H "Content-Type: application/x-www-form-urlencoded" -u <url> -fc 200
```

_data: fields to fill-up, like_ `"username=W1&password=W2"`.

---

## Options

- **-c**: colorize output.
- **-mc**: match HTTP status code with comma separated list of codes and ranges `[<x>-<y>|<x>],*` or `all`. Only display matching results.
- **-mr**: match regex. Only display matching results.
- **-fc**: filter HTTP status code with comma separated list of codes and ranges `[<x>-<y>|<x>],*`. Do not display matching results.
- **-fr**: filter regex. Do not display matching results.
- **-recursion**: scan recursively.
- **-p**: pause in seconds.
- **-rate**: rate of requests per second.