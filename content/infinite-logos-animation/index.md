---
layout: layouts/post.njk
title: An infinite logos animation
description: Using the offset property to create a CSS-only infinite logos animation
date: 2025-03-13
tags: posts
---

Another classic logos animation?! No! This one is THE real infinite ∞ logos animation. 
* Minimal HTML
* Powered by the `offset` property
* Responsive

{% image "./image.png", "CSS-only infinite logos animation" %}

```html
<div class="container">
  <img src=""><img src=""><img src=""><img src=""><img src=""><img src="">
  <svg viewBox='-152 -75 304 150'><path id="path" d='M-150 0 C-130 -150 130 150 150 0 C130 -150 -130 150 -150 0 Z'/></svg>
</div>
```

```css
@property --_w {
  syntax: '<length>';
  inherits: true;
  initial-value: min(100vw,200vh);
}
.container {
  display: grid;
  width: 300px;
  aspect-ratio: 2;
  scale: min(tan(atan2(var(--_w),350px)),3); /* for the responsive part */
}
.container > img {
  grid-area: 1/1;
  width: 35px;
  aspect-ratio: 1;
  translate: 150px 75px;
  offset: url(#path) 0% 0deg;
  animation: x 13s linear infinite;
}
@keyframes x { 
  to {offset-distance: 100%}
}
.container > :nth-of-type(2) {animation-delay:-1s}
.container > :nth-of-type(3) {animation-delay:-2s}
.container > :nth-of-type(4) {animation-delay:-3s}
.container > :nth-of-type(5) {animation-delay:-4s}
.container > :nth-of-type(6) {animation-delay:-5s}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="wBvPWwB" data-pen-title="Infinite ∞ logos animation" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBvPWwB">
  Infinite ∞ logos animation</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>