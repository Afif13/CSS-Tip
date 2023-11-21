---
layout: layouts/post.njk
title: A Tooltip Shape using 2 CSS properties
description: Only 2 CSS properties to create a simple Tooltip shape
date: 2023-11-21
tags: posts
---

The smallest code to create a simple Tooltip Shape
* One element (No pseudo-elements)
* Only 2 CSS Properties
* Optimized with CSS Variables


{% image "./image.png", "A CSS-only tooltip shape" %}

```css
.tooltip {
  /* triangle dimension */
  --b: 2em; /* base */
  --h: 1em; /* height*/

  border-image: fill 0//var(--h)
    conic-gradient(#CC333F 0 0); /* the color  */
  clip-path: 
    polygon(0 100%,0 0,100% 0,100% 100%,
      calc(50% + var(--b)/2) 100%,
      50% calc(100% + var(--h)),
      calc(50% - var(--b)/2) 100%);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ExrEXoO" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExrEXoO">
  A simple Tooltip using 2 CSS properties</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>