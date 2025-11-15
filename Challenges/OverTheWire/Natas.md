`http://natas<n>.natas.labs.overthewire.org` with username `natas<n>`.

# Level 0

Connect to `http://natas0.natas.labs.overthewire.org` with username/password `natas0`.

Password is in the source of the HTML page.

password: `0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq`.

# Level 0 -> 1

Password is in the source of the HTML page. Use Zaproxy to examine the source of the page or `curl http://natas1:0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq@natas1.natas.labs.overthewire.org`.

password: `TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI`.

# Level 1 -> 2

Page contains a 1x1 PNG image under `files/pixel.png`. File `users.txt` can be found under this directory and contains the password.

password: `3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH`.

# Level 2 -> 3

Look at `robots.txt` file. The file mention `s3cr3t` as a disallowed folder. File `users.txt` can be found under this directory and contains the password.

password: `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`.
