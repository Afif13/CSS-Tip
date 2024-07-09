---
layout: layouts/post.njk
title: Inverted border-radius using CSS mask
description: One property and 4 gradients to invert the corner of any element with a radius
date: 2024-07-09
tags: posts
---

Use CSS mask to create [an inverted radius corner](https://css-shape.com/inverted-radius/) with a minimal code.
* No extra elements
* No pseudo-elements
* Optimized with CSS variables

{% image "./image.png", "CSS-only inverted border-radius" %}

```css
img {
  --r: 25px; /* the radius */
  --s: 40px; /* the size of the corner*/
  
  width: 200px;
  border-radius: var(--r);
  --_m:/calc(2*var(--r)) calc(2*var(--r))
    radial-gradient(#000 70%,#0000 72%) no-repeat;
  mask:
    right calc(var(--s) + var(--r)) top var(--_m),
    right calc(var(--s) + var(--r)) var(--_m),
    radial-gradient(var(--s) at 100% 0,#0000 99%,#000 101%) 
     calc(-1*var(--r)) var(--r) no-repeat,
    conic-gradient(at calc(100% - var(--s) - 2*var(--r)) calc(var(--s) + 2*var(--r)),
     #0000 25%,#000 0);
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="XWLJrWE" data-pen-title="Inverted border-radius using CSS mask" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWLJrWE">
  Inverted border-radius using CSS mask</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com/)