---
layout: layouts/post.njk
title: An inner border-radius with one property
description: Use a magic border-image trick to create an inner border-radius
date: 2023-05-03
tags: posts
---

Do you want to have a radius inside the element but not outside? You can do it using only one property 🤩


{% image "./image.png", "A box with an inner border-radius" %}

```css
.box {
  --c: orange;
  --r: 50px; /* control the inner radius */
  --b: 15%;   /* control the border thickness*/

  border-image: 
    radial-gradient(
          #0000 calc(71% - var(--b)),
       var(--c) calc(72% - var(--b))
     ) 49.9%/var(--r);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="XWxexjZ" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWxexjZ">
  Inner border-radius</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


There are easier way to achieve the same result with more properties and accurate values but I wanted to share this magic one-property trick.

Related: [smashingmagazine.com/2024/01/css-border-image-property/](https://www.smashingmagazine.com/2024/01/css-border-image-property/)