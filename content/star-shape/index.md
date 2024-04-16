---
layout: layouts/post.njk
title: A Modern way to create a star shape
description: Only two properties and a 5-point polygon to create a star shape
date: 2024-04-16
tags: posts
---

Create a Star shape using clip-path and only 5 points instead of 10.

Three different codes to create the same shape
1. Precise version using math
2. Calculated version without math
3. Simplified version with easier coordinates values


{% image "./image.png", "CSS-only star shape" %}

```css
/* Accurate version with precise values */
.one {
  aspect-ratio: 1;
  clip-path: polygon(50% 0,
    calc(50%*(1 + sin(.4turn))) calc(50%*(1 - cos(.4turn))),
    calc(50%*(1 - sin(.2turn))) calc(50%*(1 - cos(.2turn))),
    calc(50%*(1 + sin(.2turn))) calc(50%*(1 - cos(.2turn))),
    calc(50%*(1 - sin(.4turn))) calc(50%*(1 - cos(.4turn))) 
   ); 
}
/* A simplified version of the previous one.
   We do the calculation and we round the result */
.two {
  aspect-ratio: 1;
  clip-path: polygon(50% 0,79% 90%,2% 35%,98% 35%,21% 90%); 
}
/* Another simplification with easier clip-path values 
   It covers a bigger area of the element */
.three {
  aspect-ratio: 1.07;
  clip-path: polygon(50% 0,80% 100%,0 39%,100% 39%,20% 100%);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="jORvmKG" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jORvmKG">
  Modern ways to create a Star shape</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>