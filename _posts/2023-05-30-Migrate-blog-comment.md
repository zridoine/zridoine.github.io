---
title: Migrate blog comment
date: 2023-05-30 11:00:30 +09:00
categories: [Blog]
tags: [blog, migrate, giscus] # TAG names should always be lowercase
---

# Migrate from utteranc to giscus

I created a GitHub blog with the help of the blog.  
However, I noticed that the comments were in white mode even when the dark mode was enabled.
![](https://velog.velcdn.com/images/jw01987/post/39134303-2ca3-44a2-bbb2-47865b8f38c4/image.png)
I was considering digging into the JavaScript code to make the necessary changes when a former team member introduced me to using giscus for commenting.  
![](https://velog.velcdn.com/images/jw01987/post/e6ee8edf-4c1a-4711-a700-696090afeb65/image.png)
It turned out to be much simpler than I thought, and using discussions instead of issues seemed like a better option.  
So, I decided to migrate from utteranc to giscus.

## Setting up Discussions category

First, go to Settings -> General -> Feature -> Discussions in the blog repository.  
Then, create a category in Discussions.
![](https://velog.velcdn.com/images/jw01987/post/fb68f2f0-b0a1-4d0a-ab5b-9d4417db8c8c/image.png)
Set the format to Announcement.
![](https://velog.velcdn.com/images/jw01987/post/fd6048e5-eb83-418e-8cb5-11165b19466d/image.png)

## Giscus Configuration

Configure [giscus](https://giscus.app) according to your preferences.  
Set the mapping to pathname and enter the category you created earlier.

```jsx
<script
  src="https://giscus.app/client.js"
  data-repo="[ENTER REPO HERE]"
  data-repo-id="[ENTER REPO ID HERE]"
  data-category="[ENTER CATEGORY NAME HERE]"
  data-category-id="[ENTER CATEGORY ID HERE]"
  data-mapping="pathname"
  data-strict="0"
  data-reactions-enabled="1"
  data-emit-metadata="0"
  data-input-position="bottom"
  data-theme="preferred_color_scheme"
  data-lang="en"
  crossorigin="anonymous"
  async
></script>
```

Make sure to keep a copy of this code.

Navigate to `_config.yml` and update the following section:

```yaml
comments:
  active: giscus # The global switch for posts comments, e.g., 'disqus'.  Keep it empty means disable
  # The active options are as follows:
  disqus:
    shortname: # fill with the Disqus shortname. › https://help.disqus.com/en/articles/1717111-what-s-a-shortname
  # utterances settings › https://utteranc.es/
  utterances:
    repo: # <gh-username>/<repo>
    issue_term: # < url | pathname | title | ...>
  # Giscus options › https://giscus.app
  giscus:
    repo: JW01987/JW01987.github.io # <gh-username>/<repo>
    repo_id:
    category:
    category_id:
    mapping: "pathname" # optional, default to 'pathname'
    input_position: "top" # optional, default to 'bottom'
    lang: # optional, default to the value of `site.lang`
    reactions_enabled: "1" # optional, default to the value of `1`
```

Fill in the details for the giscus section.

If you want to change the theme for dark mode or light mode,  
you can modify the following code in `_includes/comments/giscus.html`:

```jsx
<!-- https://giscus.app/ -->
<script type="text/javascript">
  (function () {
    const origin = 'https://giscus.app';
    const iframe = 'iframe.giscus-frame';
    const lightTheme = 'light'; // Light theme
    const darkTheme = 'dark_dimmed'; // Dark theme
```

Simply update the relevant code to make the desired changes.  
If left unmodified, the default code will be used, and no additional configuration is necessary.

## Migration Process

Go to the repository's issues.

![](https://velog.velcdn.com/images/jw01987/post/d9a29135-f1e2-4bee-a65a-29476f630720/image.png)
In this example, I've already merged them into a test repository.

![](https://velog.velcdn.com/images/jw01987/post/82457a5e-cb36-4e09-b2c5-572b7863539d/image.png)
Click on "convert to discussions."

![](https://velog.velcdn.com/images/jw01987/post/e4717d51-aa61-4131-83c9-193eeccf666a/image.png)
Place them into the desired category.

![](https://velog.velcdn.com/images/jw01987/post/a6940a92-6591-4db7-9d07-13a6d14b27c0/image.png)
Now, all the comments from the issues have been migrated!
It was great that I didn't have to click multiple times to accomplish this.

The final setup looks like this ⬇️
![](https://velog.velcdn.com/images/jw01987/post/4bd7ef8c-e28c-4093-8705-d3dc00e6a62c/image.png)
