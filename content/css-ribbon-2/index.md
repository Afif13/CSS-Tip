---
layout: layouts/post.njk
title: A CSS-only Ribbon
description: A simple code to create a fancy CSS Ribbon
date: 2023-04-24
tags: posts
---

Create a cool CSS Ribbon with a little code
* One element (no pseudo-element)
* One color definition
* No fixed width/height (It fits the content size)
* Optimized with CSS variables

{% image "./image.png", "A CSS-only Ribbon" %}

```css
.ribbon {
  --s: 70px; /* the ribbon size */
  --d: 20px; /* the depth */
  --c: 20px; /* the cutout part */
  
  padding: 0 calc(var(--s) + var(--d)) var(--d);
  background:
    conic-gradient(at left  var(--s) bottom var(--d),
     #0000 25%,#0008 0 37.5%,#0004 0) 0   /50% no-repeat,
    conic-gradient(at right var(--s) bottom var(--d),
     #0004 62.5%,#0008 0 75%,#0000 0) 100%/50% no-repeat;
  clip-path: polygon(0 var(--d), var(--s) var(--d),var(--s) 0,calc(100% - var(--s)) 0,calc(100% - var(--s)) var(--d),100% var(--d),calc(100% - var(--c)) calc(50% + var(--d)/2),100% 100%,calc(100% - var(--s) - var(--d)) 100%,calc(100% - var(--s) - var(--d)) calc(100% - var(--d)),calc(var(--s) + var(--d)) calc(100% - var(--d)),calc(var(--s) + var(--d)) 100%,0 100%,var(--c) calc(50% + var(--d)/2));
  background-color: #CC333F; /* the main color */
  /* width: fit-content; you may need to use this in your code if the element is full width */
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="QWZdXJd" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QWZdXJd">
  A CSS-only Ribbon</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

### More Ribbons

* [A Folded Ribbon To The Corner](/folded-ribbon/)
* [CSS-Only Folded Ribbon](/css-ribbon/)
