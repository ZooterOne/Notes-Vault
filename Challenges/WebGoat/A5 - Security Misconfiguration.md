# Cross-Site Request Forgeries

## Basic Get CSRF Exercise

_Challenge_: trigger the query from an external source while logged in. The response will include a _flag_.

_Solution_: use **Resend with Request Editor** and change the domain for `Referer`. Get the random flag from the response.

## Post a review on someone else’s behalf

_Challenge_: trigger a review submission on behalf of the currently logged in user.

_Solution_: use **Resend with Request Editor** and change the domain for `Referer`.
