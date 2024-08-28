---
layout: layouts/post.njk
title: Inner curve/notch shape using CSS mask
description: Create an inner curve using modern CSS and a few lines of code
date: 2024-08-28
tags: posts
---

Create an [inner curve/notch shape](https://css-shape.com/inner-curve/) using CSS mask and a few lines of code
* Only one element
* No pseudo-element
* Works with gradients & images
* Optimized with CSS variables


{% image "./image.png", "CSS only inner curve/notch shape" %}

```css
.shape {
  --r: 20px; /* control the rounded part*/
  --s: 40px; /* control the size of the cut */
  --a: 40deg; /* control the depth of the curvature*/
  
  --_m:0/calc(2*var(--r)) var(--r) no-repeat
    radial-gradient(50% 100% at bottom,#000 calc(100% - 1px),#0000);
  --_d:(var(--s) + var(--r))*cos(var(--a));
  mask:
    calc(50% + var(--_d)) var(--_m),calc(50% - var(--_d)) var(--_m),
    radial-gradient(var(--s) at 50% calc(-1*sin(var(--a))*var(--s)),
      #0000 100%,#000 calc(100% + 1px)) 0 calc(var(--r)*(1 - sin(var(--a)))) no-repeat,
    linear-gradient(90deg,#000 calc(50% - var(--_d)),#0000 0 calc(50% + var(--_d)),#000 0);
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="oNrMYRO" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/oNrMYRO">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More CSS Shapes: [css-shape.com](https://css-shape.com/)