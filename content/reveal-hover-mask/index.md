---
layout: layouts/post.njk
title: A reveal hover effect using CSS mask
description: Use CSS mask to create a nice reveal effect on hover
date: 2023-07-20
tags: posts
---

Reveal your images with a nice hover effect and a few lines of code
* No extra element (only the `<img>` tag)
* Less than 10 CSS declarations
* Powered by CSS Mask


{% image "./image.png", "A reveal hover effect using mask" %}

```css
img {
  padding: 10px; /* control the space for the gradient */
  background: repeating-linear-gradient(45deg,#FF6B6B 0 10px,#4ECDC4 0 20px);
  mask:
    radial-gradient(#000 70%,#0000 71%) content-box
    50%/var(--_s,150% 150%) no-repeat,
    linear-gradient(#000 0 0);
  mask-composite: exclude;
  transition: .5s;
  cursor: pointer;
}
img:hover {
  --_s: 0% 0%;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="abQGGew" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/abQGGew">
  Hover reveal animation using mask</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>