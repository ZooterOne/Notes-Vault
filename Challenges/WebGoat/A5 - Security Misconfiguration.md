# Cross-Site Request Forgeries

## Basic Get CSRF Exercise

_Challenge_: trigger the query from an external source while logged in. The response will include a _flag_.

_Solution_: use **Resend with Request Editor** and change the domain for `Referer`. Get the random flag from the response.

## Post a review on someone else’s behalf

_Challenge_: trigger a review submission on behalf of the currently logged in user.

_Solution_: use **Resend with Request Editor** and change the domain for `Referer`.

# XXE

## Let's try

_Challenge_: add a comment to the photo, when submitting the form try to execute an XXE injection with the comments field. Try listing the root directory of the filesystem.

_Solution_: use **Resend with Request Editor** on the POST request and change the body to `<?xml version="1.0"?><!DOCTYPE text [ <!ENTITY payloadCmd SYSTEM "file:///"> ]><comment><text>&payloadCmd;</text></comment>`.

## Modern REST framework

_Challenge_: same exercise but try to perform the same XML injection as we did in the first assignment.

_Solution_: same a before but change **Content-Type** to `application/xml`.
