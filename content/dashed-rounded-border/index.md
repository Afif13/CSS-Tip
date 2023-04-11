---
layout: layouts/post.njk
title: Circular dashed border 
description: Use mask and gradient to create a fancy dashed border
date: 2021-11-25
tags: posts
---

Create a circular dashed border with full control over the dashes. Only one element and a few lines of code are required.  Simply update the CSS variables to control the design of the border.

{% image "./dash.png", "Circular dashed border " %}


```css
.box {
  --n: 20;   /* control the number of dashes */
  --d: 8deg; /* control the distance between dashes */
  --t: 5px;  /* control the thickness of border*/
  --c: red;  /* control the coloration (can be a gradient) */
  
  width: 120px;
  aspect-ratio: 1;
  position: relative;
}
.box::after {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 50%;
  padding: var(--t);
  background: var(--c);
  mask:
      linear-gradient(#0000 0 0) content-box,
      repeating-conic-gradient(
         from calc(var(--d)/2),
         #000  0 calc(360deg/var(--n) - var(--d)),
         #0000 0 calc(360deg/var(--n))
       );
  mask-composite: intersect;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="KKvjjZN" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKvjjZN">
  Dashed border</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>