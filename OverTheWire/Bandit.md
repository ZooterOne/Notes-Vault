```
ssh bandit<n>@bandit.labs.overthewire.org -p 2220
```

# Level 0

Password is stored in a file called **readme**.

```
cat readme
```

password: `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

# Level 1

Password is stored in a file called **-**.

```
cat \-
```

password: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

# Level 2

Password is stored in a file called **--spaces in this filename--**.

```
cat -- --spaces\ in\ this\ filename--
```

password: `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

# Level 3

Password is stored in a hidden file in the **inhere** directory.

```
ls -al inhere/
cat inhere/...Hiding-From-You
```

password: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

# Level 4

Password is stored in the only human-readable file in the **inhere** directory.

```
file inhere/*
cat inhere/-file07
```

password: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

# Level 5

Password is stored in a file under the **inhere** directory and has all of the following properties:
 - human-readable
 - 1033 bytes in size
 - not executable

```
find inhere/ -size 1033c
cat inhere/maybehere07/.file2
```

password: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

# Level 6

Password is stored in somewhere on the server and has all of the following properties:
 - owned by user bandit7
 - owned by group bandit6
 - 33 bytes in size

```
find / -type f -size 33c -group bandit6 -user bandit7 2> /dev/null
cat /var/lib/dpkg/info/bandit7.password
```

password: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

# Level 7

Password is stored in the file **data.txt**, next to the word _millionth_.

```
strings data.txt | grep millionth
```

password: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

# Level 8

Password is stored in the file **data.txt** and is the only line of text that occurs only once.

```
sort data.txt | uniq -u
```

password: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

# Level 9

Password is stored in the file **data.txt**, in one of the few human-readable strings, preceded by several _=_ characters.

```
strings data.txt | grep -E '^={2,}'
```

password: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

# Level 10

Password is stored in the file **data.txt**, which contains base64 encoded data.

```
base64 -d data.txt
```

password: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

# Level 11

Password is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

```
strings data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
```

password: `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

# Level 12

Password is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed.

```
xxd -r data.txt | gzip -d | bzip2 -d | tar xz
tar xf data5.bin
tar xf data6.bin
tar xf data8.bin
cat data8.bin | gzip -d
```

password: `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

# Level 13

Password is stored in **/etc/bandit_pass/bandit14** and can only be read by user _bandit14_. A private SSH key that can be used to log into the next level is provided. 

```
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private ./
chmod 700 sshkey.private
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i sshkey.private
cat /etc/bandit_pass/bandit14
```

password: `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

# Level 14

Password can be retrieved by submitting the password of the current level to port **30000** on localhost.

```
nc localhost 30000
```

password: `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

# Level 15

Password can be retrieved by submitting the password of the current level to port **30001** on localhost using SSL/TLS encryption.

```
openssl s_client -crlf -connect localhost:30001 -servername localhost
```

password: `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

# Level 16

Password can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000.

```
nmap -p 31000-32000 -Pn -sV localhost
openssl s_client -crlf -connect localhost:31790 -servername localhost -quiet
```

password: _rsa private key_

# Level 17

Password is in **passwords.new** and is the only line that has been changed between **passwords.old** and **passwords.new**.

```
diff passwords.old passwords.new
```

password: `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

# Level 18

Password is stored in a file **readme** in the home directory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.

```
ssh bandit18@bandit.labs.overthewire.org -p 2220 sh -i
cat readme
```

password: `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

# Level 19

Password can be found in **/etc/bandit_pass**, after using the setuid binary in the home directory.

```
./bandit20-do cat /etc/bandit_pass/bandit20
```

password: `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`

# Level 20

The setuid binary in the home directory makes a connection to localhost on the specified port (command line argument). It then reads a line of text from the connection and compares it to the password of the current level. If the password is correct, it will transmit the password for the next level.

```
echo '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 4444 &
./suconnect 4444
```

password: `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

# Level 21

A program is running automatically at regular intervals from **cron**. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

```
cat /etc/cron.d/cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

password: `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`

# Level 22

A program is running automatically at regular intervals from **cron**. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

```
cat /etc/cron.d/cronjob_bandit23
cat /usr/bin/cronjob_bandit23.sh
cat /tmp/$(echo I am user bandit23 | md5sum | cut -d ' ' -f 1)
```

password: `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`

# Level 23

A program is running automatically at regular intervals from **cron**. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

```
cat /etc/cron.d/cronjob_bandit24
cat /usr/bin/cronjob_bandit24.sh
mkdir /tmp/Zoot23
chmod a+wx /tmp/Zoot23
nano /tmp/Zoot23/bandit23.sh
```

**/tmp/Zoot23/bandit23.sh**:

```
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/Zoot23/pass.txt
```

```
touch /tmp/Zoot23/pass.txt
chmod a+w /tmp/Zoot23/pass.txt
cp /tmp/Zoot23/bandit23.sh /var/spool/bandit24/foo/bandit23.sh
cat /tmp/Zoot23/pass.txt
```

password: `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`

# Level 24

A daemon is listening on port **30002** and will give you the password if given the previous password and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by brute-forcing.

```

```