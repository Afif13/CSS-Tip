---
layout: layouts/post.njk
title: Horizontal lines around your title
description: Use border-image to create Horizontal lines around a title
date: 2022-06-24
tags: posts
---

Add horizontal lines around your title using `border-image`
* No extra element
* No pseudo-element
* No overflow issue
* Only two CSS properties
* Optimized with CSS variables


{% image "./lines.png", "Titles with horizontal lines on the sides" %}

```css
h2 {
  --s: 3px;   /* the thickness */
  --c: red;   /* the color */
  --w: 100px; /* the width */
  --g: 10px;  /* the gap */
  border-image: 
    linear-gradient(
     #0000      calc(50% - var(--s)/2),
     var(--c) 0 calc(50% + var(--s)/2),
     #0000    0) 
   0 1/0 var(--w)/0 calc(var(--w) + var(--g));
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="BaYXdmM" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/BaYXdmM">
  Horizontal lines around your title</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
