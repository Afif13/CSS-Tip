---
layout: layouts/post.njk
title: Avatar hover effect with a rhombus shape
description: Add a fancy hover effect to your image with a simple code
date: 2024-10-18
tags: posts
---

Place you image inside a [rhombus shape](https://css-shape.com/rhombus/) with a cool hover effect
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 15 CSS declarations


{% image "./image.png", "CSS-only images with a rhombus shape" %}

```css
img {
  --s: 300px; /* control the size */
  
  width: var(--s);
  aspect-ratio: 1;
  object-fit: cover;
  object-position: top;
  padding: calc(var(--s)/4) calc(var(--s)/8) 0;
  box-sizing: border-box;
  background: conic-gradient(from 135deg at 50% 15%,#e0dee1,#28a6b5 25%,#0000 0);
  clip-path: polygon(-50% 0,150% 0,50% 100%);
  transition: .5s;
}
img:hover {
  padding: 0;
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="bGXRoOv" data-pen-title="Hover to select your character" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bGXRoOv">
  Hover to select your character</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>