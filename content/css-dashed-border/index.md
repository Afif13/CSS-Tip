---
layout: layouts/post.njk
title: Custom dashed border
description: Use gradient and CSS mask to create a dashed border
date: 2022-08-10
tags: posts
---

Create a custom dashed border using a few lines of code.
* No extra element
* Less than 8 CSS properties
* Easy to update using CSS variables


{% image "./dash.png", "A custom dashed border" %}

```css
.dashed {
  --b: 5px;  /* border thickness */
  --s: 30px; /* size of the dashes */
  --c1: #215A6D;
  --c2: #92C7A3;
  
  position: relative;
}
.dashed::before {
  content:"";
  position: absolute;
  inset: 0;
  padding: var(--b);
  background: 
    repeating-conic-gradient(var(--c1) 0 25%,var(--c2) 0 50%) 
    0 0/var(--s) var(--s) round;
  mask:
    linear-gradient(#000 0 0) content-box,
    linear-gradient(#000 0 0);
  mask-composite: exclude;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="WNzKJgZ" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WNzKJgZ">
  Custom dashed border</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>