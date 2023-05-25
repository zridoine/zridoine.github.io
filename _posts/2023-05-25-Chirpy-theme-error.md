---
title: Chirpy theme error
date: 2023-05-25 20:31:20 +09:00
categories: [JavaScript, Error]
tags: [javascript, error, github, jekyll] # TAG names should always be lowercase
---

# --- layout: home # Index page --- Error

## gh-pages

I encountered an error while deploying my GitHub blog with the Chirpy theme.

At first, I thought the 'gh-pages' branch was not created, so I assumed it was an error related to this.

so I change the ruby ​​version in `pages-deploy.yml`

I also attempted to install it following the solution [provided here.](https://github.com/cotes2020/jekyll-theme-chirpy/issues/628)  
(`bundle lock --add-platform x86_64-linux`)  
The error still persisted.

## Solution

A team member had the same problem as me and he gave me a solution.
![](https://velog.velcdn.com/images/jw01987/post/568b5b45-335e-42c7-8d83-4d4eeb7cc0f1/image.png)  
Go to the GitHub Actions page

![](https://velog.velcdn.com/images/jw01987/post/0a1217c0-1c01-49c6-8c3e-a480eb7fd3c9/image.png)  
Click 'Re-run all jobs'  
![](https://velog.velcdn.com/images/jw01987/post/816824d2-8f67-4600-92d8-6a2def4ef3f9/image.png)  
Then, go to the repository settings page,  
change the build value to GitHub Actions
and wait for 3 to 5 minutes and The deployment should proceed without any problems
