# Authentication Bypasses

_Challenge_: bypass the login verification method.

_Solution_: use **Resend with Request Editor** and change the body to `secQuestion3=anything&secQuestion4=anything&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746`.

# Insecure Login

_Challenge_: use a packet sniffer to intercept the login request.

_Solution_: `{"username":"CaptainJack","password":"BlackPearl"}`.

# JWT tokens

***TBC***

# Password reset

***TBC***
