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
  --r: 25px; /* radius */
  --s: 40px; /* size of the inner curve */
  
  border-radius: var(--r);
  --_m:/calc(2*var(--r)) calc(2*var(--r)) radial-gradient(#000 70%,#0000 72%) no-repeat;
  mask:
    right calc(var(--s) + var(--r)) top 0 var(--_m),
    right calc(var(--s) + var(--r)) var(--_m),
    radial-gradient(var(--s) at 100% 0,#0000 99%,#000 calc(100% + 1px)) 
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

Here is a different syntax if you want to control the offset of the inner curve.

```css
img {
  --r: 20px; /* radius */
  --s: 40px; /* size of the inner curve */
  --x: 25px; /* horizontal offset (no percentange) */
  --y: 5px;  /* vertical offset (no percentange) */
  
  border-radius: var(--r);
  --_m:/calc(2*var(--r)) calc(2*var(--r)) radial-gradient(#000 70%,#0000 72%);
  --_g:conic-gradient(at calc(100% - var(--r)) var(--r),#0000 25%,#000 0);
  --_d:(var(--s) + var(--r));
  mask:
    calc(100% - var(--_d) - var(--x)) 0 var(--_m),
    100% calc(var(--_d) + var(--y)) var(--_m),
    radial-gradient(var(--s) at 100% 0,#0000 99%,#000 calc(100% + 1px)) 
     calc(-1*var(--r) - var(--x)) calc(var(--r) + var(--y)),
    var(--_g) calc(-1*var(--_d) - var(--x)) 0,
    var(--_g) 0 calc(var(--_d) + var(--y));
  mask-repeat: no-repeat;
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="LEPBYvK" data-pen-title="Inverted border-radius using CSS mask II" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LEPBYvK">
  Inverted border-radius using CSS mask II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com/)