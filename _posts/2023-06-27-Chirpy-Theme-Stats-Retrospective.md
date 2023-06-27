---
title: Chirpy Theme Stats Retrospective
date: 2023-06-27 16:30:00 +09:00
categories: [Retrospective]
tags: [retrospective, project] # TAG names should always be lowercase
---

![](https://images.ctfassets.net/a6zo0szqvm4a/2apRmW5Bov3kaIBi3KeSa4/71f9227b86c689ea42273acdd9a3128e/guide-cover.png)

## Motivation

> [While using Velog widgets](https://github.com/eungyeole/velog-readme-stats), I wanted to display the latest posts from my GitHub blog in my README.  
> Based on that idea, I decided to create this widget.

## Development Process

The Velog widget used GraphQL to fetch data, but it was challenging to find a similar API for GitHub pages.  
So, I decided to use Rss Feed to retrieve the data.

I converted the fetched data from Rss to Json and inserted it into an SVG.

![](https://velog.velcdn.com/images/jw01987/post/572a6fe3-f5b1-467d-8250-8c1b6817ec77/image.png)

When I tested it locally, the widget displayed the recent data correctly, and the links worked as expected.

![](https://velog.velcdn.com/images/jw01987/post/bb1dcd71-a695-4c98-a737-3ebb5a32f11a/image.png)

I used Vercel as the web server.

```
[![Github Blog Stats](https://gitblog-stats.vercel.app/api?xml=<RSS LINK>)](<YOUR BLOG URL>)
```

You can use the above code to embed the widget.  
[![Github Blog Stats](https://gitblog-stats.vercel.app/api?xml=https://jw01987.github.io/feed.xml)](https://jw01987.github.io)

## Troubleshooting

### GraphQL

> I was initially confused when I opened the source code.  
> I had no knowledge of GraphQL, and it seemed unfamiliar to me.  
> So, I quickly went to learn about GraphQL through tutorials and found it relatively easy to understand.

### Rss to Json

> When I looked at the RSS data, I tried using XML to JSON libraries.  
> However, I encountered the "Non-whitespace before first tag" error regardless of which libraries I used.  
> Eventually, [I found and used the rss to json library](https://www.npmjs.com/package/rss-to-json) to resolve the issue.

### Vercel

> I tried using Vercel for the first time, and fortunately, the setup wasn't too difficult.  
> Initially, I deployed following another person's blog, but I kept encountering a 500 error.  
> So I referred [to a tutorial video](https://youtu.be/C1Sf_ntbqZQ) to help me with the deployment.

## References

[eungyeole's velog-readme-stats](https://github.com/eungyeole/velog-readme-stats)  
[MoonJuhan's tistory-readme-stats](https://github.com/MoonJuhan/tistory-readme-stats)
