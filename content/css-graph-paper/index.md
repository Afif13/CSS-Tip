---
layout: layouts/post.njk
title: CSS Graph paper pattern
description: Use CSS gradients to create a Graph paper pattern
date: 2022-06-07
tags: posts
---

Create a [Graph Paper](https://css-pattern.com/graph-paper) design using only 2 gradients

{% image "./graph.png", "A graph paper pattern" %}

```css
html {
  --s: 100px; /* control the size */
  
  --_g: #0000 90deg,#366 0;
  background: 
    conic-gradient(from 90deg at 2px 2px,var(--_g))
     0 0/var(--s) var(--s),
    conic-gradient(from 90deg at 1px 1px,var(--_g))
     0 0/calc(var(--s)/5) calc(var(--s)/5);
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="OJQoybg" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OJQoybg">
  CSS only Graph Paper </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
