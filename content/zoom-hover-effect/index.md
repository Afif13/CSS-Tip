---
layout: layouts/post.njk
title: Zoom effect on hover
description: A few lines of code to add for a zoom effect on hover
date: 2023-07-14
tags: posts
---

Add a simple zoom effect on hover for your images with a small code
* No extra element (only the `<img>` tag)
* 5 CSS declarations


```css
img {
  --f: 1.15; /* the scale factor */
  
  clip-path: inset(0);
  transition: .4s;
}
img:hover {
  clip-path: inset(calc((1 - 1/var(--f)) * 50%));
  scale: var(--f)
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="rNQJrVR" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNQJrVR">
  Zoom effect on hover (single element)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>