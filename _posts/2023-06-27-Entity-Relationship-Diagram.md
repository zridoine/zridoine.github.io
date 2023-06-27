---
title: Entity-Relationship Diagram
date: 2023-06-27 14:30:00 +09:00
categories: [SQL]
tags: [sql, erd] # TAG names should always be lowercase
---

![](https://media.licdn.com/dms/image/C5112AQGGb0EPjIt3VQ/article-cover_image-shrink_600_2000/0/1520108556981?e=2147483647&v=beta&t=ZU2nRFX6_ax1Dy3Bh6PHcSVK0BaYUFW5odysTce6mWQ)

# ERD

An Entity-Relationship Diagram (ERD) visualizes the database structure and related information in software development and database design.

# Design

![](https://velog.velcdn.com/images/jw01987/post/cc2a8eb0-95af-4d19-8e80-7e34eb7c03ad/image.png)

When designing an ERD, you need to define the following elements and create the ERD accordingly:

## E (Entity)

- Identify the entities that will hold the necessary data in the service.
- For example, entities like "User", "Post", "Comment" etc.

## A (Attribute)

- Define the attributes that each entity possesses.
- For example, the User entity can have attributes like "Name", "Login ID", "Password" etc.

## R (Relationship)

- Define the relationships between entities.
- For example, there is a relationship called "Write" between the User and Post entities.

# Arrows

![](https://lucidchart.zendesk.com/hc/article_attachments/360040355051/CardinalityGuide.png)

## One-to-One Relationship

- When an arrow has one endpoint on each side, it represents a one-to-one relationship.
- For example, there may be a one-to-one relationship between "User" and "Profile."

## One-to-Many Relationship

- When an arrow has one endpoint on one side and many endpoints on the other side, it represents a one-to-many relationship.
- For example, there may be a one-to-many relationship between "Post" and "Comment."
  - One post can have multiple comments, but each comment belongs to only one post.

## Many-to-Many Relationship

- When arrows have many endpoints on both sides, it represents a many-to-many relationship.
- Many-to-many relationships are typically implemented through intermediate tables.
- For example, there may be a many-to-many relationship between "Student" and "Subject" entities.
  - A student can take multiple subjects, and each subject can be taken by multiple students.

## Zero or ...

- Indicates that a relationship may or may not exist.
- It means that an entity instance can have zero or more relationships with other entity instances.
- For example, a "Post" may or may not have any "Comment."

## One and One and Only One

![](https://i.stack.imgur.com/lRUbs.png)

### One

- Student A can be assigned to only one dormitory room.
- Dormitory room 200 is a single room, accommodating only one student.
- Next year, Student A will be assigned to a new dormitory room, and room 200 will be assigned to a new student.

### One and Only One

- Student A can have only one ID (e.g., a11235), and only Student A can log in with that ID.
- If Student A graduates, no other student can be assigned the same ID (a11235).

[Reference](https://stackoverflow.com/questions/33781451/crows-feet-one-vs-one-and-only-one)
