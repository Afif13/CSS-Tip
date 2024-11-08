---
layout: layouts/post.njk
title: Folded rectangle shapes using CSS mask
description: Create a folded rectangle shape with minimal code and a subtle 3D effect
date: 2024-11-08
tags: posts
---

Create [folded rectangle shapes](https://css-shape.com/folded-rectangle/) with a subtle 3D effect
* Single element (no pseudo-element)
* Optimized with CSS Variables
* Powered by CSS mask


{% image "./image.png", "CSS only folded rectangle shapes" %}

```css
.folded {
  --r: 30px; /* control the folded part */
  
  background: 
    linear-gradient(90deg,#0007,#0000 calc(var(--r)/2) calc(100% - var(--r)/2),#0007) 
    #88C425;
  border-radius: 0 0 var(--r) var(--r);
  --_m:0,#0000 100%,#000 calc(100% + 1px);
  mask:
    radial-gradient(var(--r) at 100% var(--_m)) no-repeat,
    radial-gradient(var(--r) at 0    var(--_m)) 100% 0 no-repeat,
    linear-gradient(#0000 var(--r),#000 0);
  mask-size: var(--r);
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="eYqQZqj" data-pen-title="CSS-only folded rectangle shapes" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/eYqQZqj">
  CSS-only folded rectangle shapes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com)