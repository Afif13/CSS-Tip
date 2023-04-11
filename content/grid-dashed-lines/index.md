---
layout: layouts/post.njk
title: Grid with dashed lines
description: Two gradients to create a grid with dashed lines
date: 2022-02-28
tags: posts
---

Create a grid of dashed lines using a few lines of code
* Two properties
* Two gradients
* Easy to adjust using CSS variables

{% image "./dash.png", "A grid of dashed lines" %}

```css
html {
  --c1: black;  
  --c2: pink;  
  --s: 100px;  /* control the size of the grid */
  --n: 4;      /* control the number of dashes*/
  --t: 3px;    /* the thickness of dashes */
  --g: 10px;   /* the gap between dashes */
  
  --_d:calc(var(--s)/var(--n));
  background: 
    conic-gradient(from 90deg at var(--t) var(--t),var(--c2) 90deg,#0000 0) 
     calc(-1*var(--t)) calc(-1*var(--t)) / var(--s) var(--s),
    conic-gradient(from 90deg at var(--g) var(--g),var(--c1) 90deg,var(--c2) 0) 
     calc((var(--_d) + var(--g) + var(--t))/-2) 
     calc((var(--_d) + var(--g) + var(--t))/-2) 
    / var(--_d) var(--_d);
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ExbdwGJ" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExbdwGJ">
  CSS-only Grid of dashed lines</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>