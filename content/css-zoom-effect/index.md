---
layout: layouts/post.njk
title: CSS-only Zoom effect on images
description: clip-path and transform to create a zoom effect
date: 2022-02-28
tags: posts
---

Apply a zoom effect to your image with a few lines of code:
* No extra element (only the `<img>` tag)
* No duplicated images
* Only three CSS properties
* Easy to adjust using CSS variables

{% image "./zoom.png", "A zoom effect on images" %}

```css
img {
  --zoom: 1; /* control the zoom level */
  /* the coordinate of the zoom */
  --x: 50%;
  --y: 50%;
  /**/
  transform: scale(var(--zoom));
  transform-origin: var(--x) var(--y);
  clip-path: inset(
    calc((1 - 1/var(--zoom)) * (var(--y)))
    calc((1 - 1/var(--zoom)) * (100% - var(--x)))
    calc((1 - 1/var(--zoom)) * (100% - var(--y)))
    calc((1 - 1/var(--zoom)) * (var(--x)))
  );
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="MWOOMEP" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWOOMEP">
  CSS only zoom effect on image</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [verpex.com/blog/website-tips/how-to-make-a-zoom-effect-using-css](https://verpex.com/blog/website-tips/how-to-make-a-zoom-effect-using-css)