---
layout: layouts/post.njk
title: Better text wrapping using text-wrap
description: The text-wrap property allows you to control how text is wrapped
date: 2024-06-10
tags: posts
---


Enhance your text wrapping using `text-wrap`. No more lonely words at the end of paragraphs, and titles will look much better.

```css
* {
  text-wrap: pretty;
}
h1,h2,h3,h4,h5,h6 {
  text-wrap: balance;
  /* it works well with text-align: center */
}
```

{% image "./image.png", "Showing the effect of text-wrap" %}
