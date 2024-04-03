---
layout: layouts/post.njk
title: Grid with dashed lines
description: Two gradients to create a grid with dashed lines
date: 2022-02-28
tags: posts
---

Create a grid of dashed lines using a few lines of code
* One property
* Two gradients
* Easy to adjust using CSS variables

{% image "./image.png", "A grid of dashed lines" %}

```css
html {
  --s: 100px;  /* control the size of the grid */
  --n: 4;      /* control the granularity */
  --t: 2px;    /* the thickness */
  --g: 10px;   /* the gap between dashes */
  
  --c:#556270 25%,#0000 0;
  background: 
    conic-gradient(at var(--g) var(--t),var(--c))
     calc((var(--s)/var(--n) - var(--g) + var(--t))/2) 0/
     calc(var(--s)/var(--n)) var(--s),
    conic-gradient(from 180deg at var(--t) var(--g),var(--c))
     0 calc((var(--s)/var(--n) - var(--g) + var(--t))/2)/
     var(--s) calc(var(--s)/var(--n));
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ExbdwGJ" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExbdwGJ">
  CSS-only Grid of dashed lines</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>