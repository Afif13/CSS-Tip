---
layout: layouts/post.njk
title: A CSS-only 3D Zig-Zag edge
description: A simple code to create a cool Zig-Zag edge with a 3D effect
date: 2023-04-19
tags: posts
---

Create a nice 3D Zig-Zag edge with a simple code:
* One element (No pseudo-element)
* Two gradients
* One color definition
* Optimized with CSS variables

{% image "./image.png", "A CSS-only 3D Zig Zag edge" %}

```css
.bottom {
  --_m: from 45deg at bottom;
  padding-bottom: var(--s);
  background: 
    conic-gradient(var(--_m) var(--d) left 50%,
      #0004 135deg,#0009 0 270deg,#0000 0) 
    50%/var(--s);
}
.top {
  --_m: from -135deg at top;
  padding-top: var(--s);
  background: 
    conic-gradient(var(--_m) var(--d) left 50%,
      #0009 135deg,#0004 0 270deg,#0000 0) 
    50%/var(--s);
}
.top,
.bottom {
  --s: 81px; /* control the size */
  --d: 20px; /* control the depth */
  
  mask: conic-gradient(var(--_m),#0000 75%,#000 0) 50%/var(--s);
  background-color: #ED303C; /* the main color */
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="XWxjMBd" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWxjMBd">
  CSS-only 3D zig-zag edge </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More CSS Shapes: [css-shape.com](https://css-shape.com)