---
layout: layouts/post.njk
title: A single-element spinner loader
description: A mask trick to create a simple CSS loader with a single element
date: 2022-02-02
tags: posts
---

Create a spinner loader using one element and less than 10 CSS declarations

{% image "./loader.png", "A CSS-sonly spinner loader" %}

```css
.loader {
  width: 120px;        /* the size */
  padding: 15px;       /* the border thickness */
  background: #07e8d6; /* the color */
  
  aspect-ratio: 1;
  border-radius: 50%;
  mask: 
    conic-gradient(#0000,#000) subtract,
    conic-gradient(#000 0 0) content-box;
  animation: load 1s linear infinite;
}
@keyframes load {
  to{rotate: 1turn}
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zYPqMgq" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYPqMgq">
  Spinner loader</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More loaders: [css-loaders.com](https://css-loaders.com/)