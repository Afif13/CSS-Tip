---
layout: layouts/post.njk
title: A color wheel with an array of colors
description: A simple conic-gradient() trick to create a color wheel
date: 2023-07-18
tags: posts
---

Create a perfect color wheel with multiple colors using `conic-gradient()`
* One variable to define all the colors
* No color duplication
* Smooth transition between all the colors


{% image "./image.png", "A color wheel using conic-gradient" %}

```css
.box {
   /* your colors without duplication */
  --colors: green,yellow,red,blue,pink;

  background: conic-gradient(var(--colors) 0,var(--colors));
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="NWEMdvw" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/NWEMdvw">
  Color wheel with colors array</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
