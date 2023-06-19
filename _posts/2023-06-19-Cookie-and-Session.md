---
title: Cookie and Session
date: 2023-06-19 14:05:00 +09:00
categories: [Computer Science]
tags: [cs, cookie, session] # TAG names should always be lowercase
---

# 🍪 Cookie

Cookie are data sent as part of the Response. The server bakes the cookie and sends them to the browser in the Response. The browser, if it has the cookie, includes them in subsequent communications with the server (Request).

One drawback of using cookie is that if the communication is not done over HTTPS, the frontend can manipulate the cookie freely.

# 🔑 Session

Session data is stored on the server (like a lock 🔒). Each data has a unique session ID (a key 🔑) associated with it. This ID is exchanged using cookie, resolving the security vulnerabilities of cookie.
(Cookie store data directly, while sessions only hold the keys, which users possess.)

However, since all authentication is handled by the server (matching keys to locks 🔐), as the number of users increases, the server can become overloaded with the processing, leading to potential issues.
