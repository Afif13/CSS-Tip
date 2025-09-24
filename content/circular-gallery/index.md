---
layout: layouts/post.njk
title: Circular Gallery of Rounded Images
description: A fancy gallery of images created with few lines code
date: 2025-08-19
tags: posts
---

In a previous post, we saw [how to place images around a circle](/images-circle/). We can use the same trick to create a circular gallery of images. Thanks to a combination of `:nth-child` and [`sibling-index()`](https://css-tip.com/element-index/), we need fewer than 10 CSS declarations to correctly place up to 61 images.

{% image "./image.png", "CSS-only circular gallery of images" %}


```css
.container {
  display: inline-grid;
}
.container img {
  --s: 85px; /* image size */
  
  width: var(--s);
  grid-area: 1/1;
  border-radius: 50%;
}
/* up to 7 images (1 + 6)*/
.container img:nth-child(n + 2) {
  offset: circle(calc(1.15*var(--s))) calc(100%*sibling-index()/6) 0deg;
}
/* up to 19 images (1 + 6 + 12) */
.container img:nth-child(n + 8) {
  offset: circle(calc(2.2*var(--s))) calc(100%*sibling-index()/12 + 4.16%) 0deg;
}
/* up to 37 images (1 + 6 + 12 + 18) */
.container img:nth-child(n + 20) {
  offset: circle(calc(3.3*var(--s))) calc(100%*sibling-index()/18 + 2.77%) 0deg;
}
/* up to 61 images (1 + 6 + 12 + 18 + 24) */
.container img:nth-child(n + 38) {
  offset: circle(calc(4.4*var(--s))) calc(100%*sibling-index()/24 + 2.08%) 0deg;
}
```

⚠️ Limited support (Chrome only for now) ⚠️

<p class="codepen" data-height="750" data-default-tab="result" data-slug-hash="XJmZoEO" data-pen-title="Circular gallery of images" data-preview="true" data-user="t_afif" style="height: 750px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XJmZoEO">
  Circular gallery of images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

And here is an animated version

<p class="codepen" data-height="750" data-default-tab="result" data-slug-hash="pvjaMMx" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 750px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/pvjaMMx">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>