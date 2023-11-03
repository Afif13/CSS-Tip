---
layout: layouts/post.njk
title: An Infinite Ribbon Shape for your title
description: Transform your title into an infinite ribbon shape using CSS
date: 2023-11-03
tags: posts
---

Transform your title into an Infinite Ribbon Shape using a few lines of code
* Only one element 
* No pseudo-elements
* No overflow issue

{% image "./image.png", "CSS only infinite ribbon shapes" %}

```css
.ribbon {
  --r: .8em; /* control the cutout */
  --c: #bd1550;
  
  padding-inline: 1lh calc(var(--r) + .25em);
  border-image: conic-gradient(var(--c) 0 0) fill 0//9999px;
  outline: 9999px solid #0004;
}
.top {
  clip-path: polygon(1lh 100%,100% 100%,calc(100% - var(--r)) 50%,100% 0,1lh 0,1lh -9999px,0 -9999px,0 0);
}
.bottom {
  clip-path: polygon(1lh 0,100% 0,calc(100% - var(--r)) 50%,100% 100%,1lh 100%,1lh 9999px,0 9999px,0 100%);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="NWoRJMy" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/NWoRJMy">
  Infinite Ribbon Shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Ribbon Shapes: [css-generators.com/ribbon-shapes](https://css-generators.com/ribbon-shapes/)