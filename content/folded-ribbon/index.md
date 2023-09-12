---
layout: layouts/post.njk
title: A folded ribbon to the corner
description: Add a folded ribbon to the corner of your element with a simple code
date: 2023-05-12
tags: posts
---

Add a folded ribbon to the corner of your container using a few lines of code
* One element (no pseudo-element)
* No fixed width/height (fit content size)
* No magic positioning numbers
* Easy switch between both positions

{% image "./image.png", "A CSS folded ribbon" %}

```css
.ribbon {
  --f: 15px; /* control the folded part */
  
  position: absolute;
  top: 0;
  background: #45ADA8; /* the main color  */
  border-bottom :var(--f) solid #0007;
  clip-path: polygon(
    100% calc(100% - var(--f)),100% 100%,calc(100% - var(--f)) calc(100% - var(--f)),var(--f) calc(100% - var(--f)), 0 100%,0 calc(100% - var(--f)),999px calc(100% - var(--f) - 999px),calc(100% - 999px) calc(100% - var(--f) - 999px))
}
.right {
  right: 0;
  transform: translate(calc((1 - cos(45deg))*100%), -100%) rotate(45deg);
  transform-origin: 0% 100%;
}
.left {
  left: 0;
  transform: translate(calc((cos(45deg) - 1)*100%), -100%) rotate(-45deg);
  transform-origin: 100% 100%;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="rNqKmvN" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rNqKmvN">
  CSS-only folded ribbon</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

### More Ribbons

* [A CSS-Only Ribbon](/css-ribbon-2/)
* [CSS-Only Folded Ribbon](/css-ribbon/)
