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

Click **View Profile** and use **Resend with Request Editor** and:
1. Manually try different ids. Id to find is `2342388`. Alternatively use **Attack | Fuzz** to automatically increment the id within a range.
2. Change the `Method` to `PUT`, the `URL` to indicate the user id (`2342388`), the `Content-Type` to `application/json` and edit the body to `{"userId":"2342388","color":"red"}`.

---
# Missing Function Level Access Control

## Relying on obscurity

Using **Developer Tools**, parse css files and find `hidden-menu-item` in **ac.css**, which hides element. Search for `hidden-menu-item` in the html source. Hidden items are `Users` and `Config`.

## Gathering User Info

Click **Submit** and use **Resend with Request Editor** with the following changes:
- Change the `Method` to `GET`.
- Change the end-point of the `URL` to `users`.
- Add `Content-Type: application/json; charset=UTF-8`.

Hash to find is `SVtOlaa+ER+w2eoIIVE5/77umvhcsh5V8UyDLUa1Itg=`.

## The company fixed the problem, right?

Use **Resend with Request Editor** on the previous request with the following changes:
- Change the `Method` to `POST`.
- Add `{ "username" : "<Username>", "admin" : true, "userHash" : "" }` in the body.
This will add our created username to the admin list. Then modify the `GET` request using `users-admin-fix` as the end-point of the `URL`.

Hash to find is `d4T2ahJN4fWP83s9JdLISio7Auh4mWhFT1Q38S6OewM=`.