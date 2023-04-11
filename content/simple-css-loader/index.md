---
layout: layouts/post.njk
title: A simple CSS loader
description: A mask trick to create a simple loader
date: 2022-02-02
tags: posts
---

Create a CSS-only loader with a simple code. 
* One `<div>`
* Less than 10 CSS declarations

{% image "./loader.png", "A CSS only loader" %}

```css
.loader {
  width: 120px;        /* the size */
  padding: 15px;       /* the border thickness */
  background: #07e8d6; /* the color */
  
  aspect-ratio: 1;
  border-radius: 50%;
  mask: 
    conic-gradient(#0000,#000),
    linear-gradient(#000 0 0) content-box;
  mask-composite: subtract;
  box-sizing: border-box;
  animation: load 1s linear infinite;
}

@keyframes load {
  to{transform: rotate(1turn)}
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zYPqMgq" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYPqMgq">
  Spinner loader</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>