---
title: What is middleware?
date: 2023-06-22 21:00:00 +09:00
categories: [Computer Science]
tags: [cs, middleware] # TAG names should always be lowercase
---

![](https://tighten.com/assets/images/insights/intro-to-terminable-middleware-diagram.jpeg)

# Middleware

Middleware is a function that operates between the request and response in an application, hence the name "middle-ware." It sits in the middle and functions between the two.

- Manipulation: Middleware can inspect request headers or add specific headers to the response.

  - For example, a middleware can check the validity of an authentication token by inspecting the headers.

- Adding an intermediate step: Middleware can perform additional actions during request or response processing.

  - For instance, a middleware can check the user's authentication status before accessing a page that requires login, such as a user's profile or an admin page.
  - It can also validate data and send error responses if errors are detected.

- Cycle control: Middleware has control over the cycle between the request and the response.
  - For example, a middleware can record the time when a request occurs and add it to the response headers.
  - It can also perform logging for incoming requests.

# How to use Middleware

```js
app.use((req, res, next) => {
  // Code to be executed in the middle
});
```

- `next`: Calls the next middleware function defined in the stack.
- If multiple middleware functions overlap, they will be entered sequentially starting from the first middleware.
- If `next()` is not called during the execution of a middleware, the next middleware will not be executed.
