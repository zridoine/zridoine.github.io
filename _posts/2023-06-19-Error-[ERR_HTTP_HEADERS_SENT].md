---
title: Error [ERR_HTTP_HEADERS_SENT]
date: 2023-06-19 13:58:00 +09:00
categories: [MongoDB, Error]
tags: [mongodb, error] # TAG names should always be lowercase
---

# Error [ERR_HTTP_HEADERS_SENT]: Cannot set headers after they are sent to the client.

```js
// Create a comment
router.post("/comment", async (req, res) => {
  const { postId, content, commentId } = req.body;

 ...

  // Check if the comment ID already exists
  const commentIdFind = await Comment.find({ commentId });
  if (!commentIdFind.length) {
    res
      .status(400)
      .json({ success: false, msg: "The specified comment ID already exists." });
  }

  await Comment.create({
    postId,
    content,
    commentId,
  });

  res.status(200).json({ success: true, msg: "The comment has been registered." });
});
```

This error occurs when the response headers are being sent to the client multiple times. It seems that you may have missed using the "return" statement in your "if" statements.

By not using "return", the execution continues to the next line, causing multiple responses to be sent and resulting in the mentioned error.

To resolve this issue, make sure to add the "return" statement after sending the response in each "if" statement.

Remember to include the "return" statement to ensure that the response is sent and the execution stops after each "if" statement.

```js
// Create a comment
router.post("/comment", async (req, res) => {
  const { postId, content, commentId } = req.body;

 ...

  // Check if the comment ID already exists
  const commentIdFind = await Comment.find({ commentId });
  if (!commentIdFind.length) {
    return res
      .status(400)
      .json({ success: false, msg: "The specified comment ID already exists." });
  }

  await Comment.create({
    postId,
    content,
    commentId,
  });

  res.status(200).json({ success: true, msg: "The comment has been registered." });
});
```
