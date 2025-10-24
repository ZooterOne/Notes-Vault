# Hijack a session

1. Manually send the POST request multiple times and observe the value for `hijack_cookie` in the response. This is composed of two parts: ID-TIMESTAMP.
2. When the id has a jump, use the missing id with the previous timestamp and re-send the request adding `hijack_cookie=ID-TIMESTAMP;` to the `Cookie` field.

---
# Insecure Direct Object References

## Observing Differences & Behaviors

Look at the GET response to find the hidden attributes. Those attributes are `role,userId`.

## Guessing & Predicting Patterns

Alternate URL to view profile is `WebGoat/IDOR/profile/2342384`.

## Playing with the Patterns

Use `Resend with Request Editor` and
1. Manually try different ids. Id to find is `2342388`. Alternatively use `Attack | Fuzz` to automatically increment the id within a range.
2. Change the `Method` to `PUT`, the `URL` to indicate the user id (`2342388`), the `Content-Type` to `application/json` and edit the body to `{"userId":"2342388","color":"red"}`.

---
# Missing Function Level Access Control

## Relying on obscurity

Parse css files and find `hidden-menu-item` in **ac.css**, which hides element. Search for `hidden-menu-item` in the html source. Hidden items are `Users` and `Config`.

