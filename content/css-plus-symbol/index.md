---
layout: layouts/post.njk
title: CSS-only plus/cross icon
description: Use one element and one gradient to create a plus/cross icon
date: 2021-11-04
tags: posts
---

Create a plus icon ➕ or a cross icon ✖️  

* One element 
* No Pseudo element
* One gradient
* Easily adjust the size and coloration

{% image "./image.png", "CSS-only cross/plus icon" %}


```css
.plus {
  --b: 10px;   /* the thickness*/
  --c: #0000 90deg,#000 0; /* the coloration */
  width: 50px; /* the size */
  aspect-ratio: 1;
  background:
    conic-gradient(from 90deg at var(--b) var(--b),var(--c)) 
    calc(100% + var(--b)/2) calc(100% + var(--b)/2)/
    calc(50%  + var(--b))   calc(50%  + var(--b));
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="yLopXQB" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLopXQB">
  Plus symbol /Cross Symbol</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>