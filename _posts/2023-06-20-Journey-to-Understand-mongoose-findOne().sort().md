---
title: Journey to understanding mongoose findOne().sort()
date: 2023-06-20 15:20:00 +09:00
categories: [MongoDB, Mongoose]
tags: [mongodb, mongoose] # TAG names should always be lowercase
---

# Why Sort in findOne?

While listening to a lecture, I came across the following code snippet:

```js
const maxOrderByUserId = await Todo.findOne().sort("-order").exec();
```

This code retrieves the data with the highest "order" value by sorting in descending order based on the "order" field.

But I've read it left->right in order so far, so I really didn't understand findOne()
You're pulling one out, but you're aligning it from there?

So, I decided to experiment with the following code:

```js
const maxOrderByUserId = await Todo.sort("-order").findOne().exec();
```

But it resulted in an error:

```js
TypeError: Todo.sort is not a function
```

## Cursor...?

Upon researching, I found that in Mongoose, the sort() method should be preceded by a cursor value. [(Source: Mongoose Query Sort Documentation)](<https://mongoosejs.com/docs/api/query.html#Query.prototype.sort()>)

It seems that find() typically returns a cursor value. [(Source: Mongoose Aggregate Cursor Documentation)](<https://mongoosejs.com/docs/api/aggregate.html#Aggregate.prototype.cursor()>)

Understanding what exactly a cursor is proved to be difficult for me...

Anyway, it seems that the sort should come after the cursor value.

# How about using find, sort, and limit instead?

This led me to another curiosity: since findOne() is used to retrieve a single item, wouldn't using find() with limit(1) achieve the same result?

```js
const maxOrderByUserId = await Todo.find().sort("-order").limit(1).exec();
```

However, this also resulted in an error:

```js
ValidationError: Todo validation failed: order: Cast to Number failed for value "NaN" (type number) at path "order"
```

The `maxOrderByUserId.order` value turned out to be undefined instead of a number.

I couldn't understand why...

In the original lecture code, the type was correctly detected as a number:

```js
const maxOrderByUserId = await Todo.find();
console.log(typeof maxOrderByUserId.order); // undefined

const maxOrderByUserId = await Todo.findOne();
console.log(typeof maxOrderByUserId.order); // number
```

## What a fool I am!

I couldn't understand it, so I asked around.....

![](https://velog.velcdn.com/images/jw01987/post/7298a842-2bf4-4f2b-9e23-5a04bbc87cd7/image.png)

> The find() method retrieves an array of objects, even if it is limited to only one item. So, even when limiting the result to one item, it will still be wrapped in an array and accessible at index 0.

> To access the value at index 0, you can use parentheses to wrap the variable name, or access it directly using test[0].order.

> By doing so, the type will be correctly detected as a number. 🙂

Oh...?
![](https://t1.daumcdn.net/brunch/service/user/A1Z/image/w82VKz4-i4tTWXpI-mU9FP4J8lg.jpeg)

```js
const maxOrderByUserId = await Todo.find();
console.log(typeof maxOrderByUserId[0].order); // number
```

Oh...?

Wow, I was really being foolish...

# Conclusion

```js
const maxOrderByUserId = await Todo.find().sort("-order").limit(1).exec();
const maxOrderByUserId = await Todo.findOne().sort("-order").exec();
```

These two code snippets achieve the same result. The time it takes to execute them will likely be similar.  
Let's use something that suits our taste...
