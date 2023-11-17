---
layout: layouts/post.njk
title: Add a 3D style to your text II
description: Add a touch of 3D to your text with some gradients tricks
date: 2023-11-17
tags: posts
---

Another concept of 3D text with a minimal code
* Only one element (no pseudo-elements)
* Works with multi-line text
* Optimized with CSS variables


{% image "./image.png", "A 3D text using CSS" %}

```css
h2 { 
  --d: .3em; /* control the depth */
  --s: .2em; /* control the space between boxes */
  line-height: 2; /* control the height of the boxes */

  padding-inline: .2em calc(var(--d) + .2em);
  padding-bottom: calc(var(--d)/2);
  clip-path: inset(calc(var(--d)/2) 0 0);
  background:
    conic-gradient(at calc(100% - var(--d)) calc(100% - var(--d)),
      #0004 37.5%,#0008 0 75%,#0000 0)
    0 calc((var(--d) - var(--s))/2)/100% 1lh 
    #d81a14; /* the main color */
  mask:
    conic-gradient(from -90deg at calc(100% - var(--d)) var(--s),#0000 62.5%,#000 0)
     100% calc((var(--d) - var(--s))/2)/51% 1lh repeat-y,
    conic-gradient(from  90deg at var(--d) calc(100% - var(--s)),#0000 62.5%,#000 0) 
     0    calc((var(--d) + var(--s))/2)/51% 1lh repeat-y;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="bGzawKP" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bGzawKP">
  CSS only 3D multi-line text II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>