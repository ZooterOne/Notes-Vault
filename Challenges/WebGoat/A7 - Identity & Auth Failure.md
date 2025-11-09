# Authentication Bypasses

_Challenge_: bypass the login verification method.

_Solution_: use **Resend with Request Editor** and change the body to `secQuestion3=anything&secQuestion4=anything&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746`.

# Insecure Login

_Challenge_: use a packet sniffer to intercept the login request.

_Solution_: `{"username":"CaptainJack","password":"BlackPearl"}`.

# JWT tokens

## Decoding a JWT token

_Challenge_: decode the following JWT token and find the user.

```
eyJhbGciOiJIUzI1NiJ9.ew0KICAiYXV0aG9yaXRpZXMiIDogWyAiUk9MRV9BRE1JTiIsICJST0xFX1VTRVIiIF0sDQogICJjbGllbnRfaWQiIDogIm15LWNsaWVudC13aXRoLXNlY3JldCIsDQogICJleHAiIDogMTYwNzA5OTYwOCwNCiAgImp0aSIgOiAiOWJjOTJhNDQtMGIxYS00YzVlLWJlNzAtZGE1MjA3NWI5YTg0IiwNCiAgInNjb3BlIiA6IFsgInJlYWQiLCAid3JpdGUiIF0sDQogICJ1c2VyX25hbWUiIDogInVzZXIiDQp9.9lYaULTuoIDJ86-zKDSntJQyHPpJ2mZAbnWRfel99iI
```

_Solution_: use `https://www.jwt.io/` to decode the token. This give:

_Header_

```
{
  "alg" : "HS256"
}
```

_Payload_

```
{
  "authorities" : [ "ROLE_ADMIN", "ROLE_USER" ],
  "client_id" : "my-client-with-secret",
  "exp" : 1607099608,
  "jti" : "9bc92a44-0b1a-4c5e-be70-da52075b9a84",
  "scope" : [ "read", "write" ],
  "user_name" : "user"
}
```

## JWT signing

_Challenge_: try to change the token you receive and become an admin user by changing the token and once you are admin reset the votes.

_Solution_: login as **Tom** and get the token. Decode the token using `https://www.jwt.io/` and change `alg`  to `none` and `admin` to `true`. This gives the following token `eyJhbGciOiJub25lIn0.eyJpYXQiOjE3NjM1MzgyNzEsImFkbWluIjoidHJ1ZSIsInVzZXIiOiJUb20ifQ.` Using **Requester** send the **POST** request to reset the votes, using this new token under `Cookie: access_token=`.

## Code review

_Q_: What is the result of the first code snippet?

_A_: Solution 1: Throws an exception in line 12

_Q_: What is the result of the second code snippet?

_A_: Solution 2: Invoked the method removeAllUsers at line 7

# Password reset

## Security questions

_Challenge_: users can retrieve their password if they can answer the secret question properly. There is no lock-out mechanism on this **Forgot Password** page. Your username is `webgoat` and your favorite color is `red`. The goal is to retrieve the password of another user. Users you could try are: **tom**, **admin** and **larry**.

_Solution_: Use **Attack | Fuzz** on the **POST** request for user **webgoat**. Fuzz `username` and `securityQuestion`. Found secret questions are `tom/purple`, `admin/green` and `larry/yellow`.
