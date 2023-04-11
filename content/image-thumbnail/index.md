---
layout: layouts/post.njk
title: "One big image + thumbnails"
description: A CSS grid with a big image and thumbnails
date: 2021-12-15
tags: posts
---

A big image + thumbnails using CSS Grid. Same code for both the horizontal and vertical layout.

{% image "./image.png", "A big image plus thumbnail" %}


```html
<div class="grid">
  <img src="" alt="">
  <img src="" alt="">
  <img src="" alt="">
</div>
```

```css
.grid {
  display: grid;
  grid-auto-flow: row; /* it's the default value (can be omitted) */
}
.horizontal {
  grid-auto-flow: column;
}
.grid img:first-child {
  grid-area: span 3 / span 3;
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="xxLYLNW" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xxLYLNW">
  Big Image + thumbnails</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [css-tricks.com/exploring-css-grids-implicit-grid-and-auto-placement-powers](https://css-tricks.com/exploring-css-grids-implicit-grid-and-auto-placement-powers/)