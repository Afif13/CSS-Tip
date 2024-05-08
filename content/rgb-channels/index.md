---
layout: layouts/post.njk
title: How to extra R,G,B Channels from a color
description: Use the relative syntax color to extra R,G,B Channels
date: 2024-05-08
tags: posts
---

Using the new [relative color syntax](https://developer.chrome.com/blog/css-relative-color-syntax), you can easily extract the R,G,B channels of any color and use them as separate colors.

Useful when you want to do some color manipulation.


```css
:root {
  --c: #BD1550; /* the main color */
  
  /* the R,G,B channels as separate colors */
  --R: rgb(from var(--c) r 0 0);
  --G: rgb(from var(--c) 0 g 0);
  --B: rgb(from var(--c) 0 0 b);
}
```
