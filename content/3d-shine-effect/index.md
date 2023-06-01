---
layout: layouts/post.njk
title: 3D shine effect on hover
description: A fancy 3D effect with a shiny animation on hover 
date: 2023-06-01
tags: posts
---

Add a 3D effect to your image with a shiny animation on hover ✨
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 10 CSS declrations


{% image "./image.png", "A 3D shine effect on image" %}

```css
img {
  --a: 8deg; /* control the angle of rotation (the smaller, the better) */
  aspect-ratio: 1;
  transform: perspective(400px) rotate3d(var(--i,1,-1),0,var(--a));
  mask: 
    linear-gradient(135deg,#000c 40%,#000,#000c 60%)
    100% 100%/240% 240%;
  transition: .4s;
}
img:hover {
  --i:-1,1;
  mask-position: 0 0;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="VwEJqKV" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/VwEJqKV">
  3D Shine effect on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

