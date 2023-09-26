---
layout: layouts/post.njk
title: Folded Ribbon Shape with hover effect II
description: a fancy ribbon shape with a nice hover effect
date: 2023-09-26
tags: posts
---

Create a fancy ribbon shape with a few lines of code
* Only one element
* No pseudo-elements
* Optimized with CSS variables
* Nice animation on hover


{% image "./image.png", "A folded ribbon shape using CSS" %}

```css
h1 {
  --r: 20px; /* control the cutout of the ribbon */
  --s: 20px; /* size of the folded part */
  --c: #d81a14;
  
  --d: 0px; /* This will control the animation part */
  line-height: 1.6; /* control the height */
  padding-inline: 1.2lh;
  color: #fff;
  background: var(--c);
  box-shadow: 0 0 0 999px color-mix(in srgb,var(--c),#000 35%);
  clip-path: polygon(var(--d) 0,var(--d) calc(0% - var(--s) - var(--r) - var(--d)),calc(.5lh + var(--d)) calc(0% - var(--s) - var(--d)),calc(1lh + var(--d)) calc(0% - var(--s) - var(--r) - var(--d)),calc(1lh + var(--d)) 0,calc(100% - 1lh - var(--d)) 0,calc(100% - var(--d)) 100%,calc(100% - var(--d)) calc(100% + var(--r) + var(--s) + var(--d)),calc(100% - .5lh - var(--d)) calc(100% + var(--r) + var(--d)),calc(100% - 1lh - var(--d)) calc(100% + var(--r) + var(--s) + var(--d)),calc(100% - 1lh - var(--d)) 100%,calc(1lh + var(--d)) 100%);
  transition: .3s linear;
}
h1:hover {
  --d: .2lh; /* don't use a big value to not cut the text */
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="NWeYQpN" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/NWeYQpN">
  CSS-only folded ribbon (with hover effect)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Ribbon Shapes: [css-generators.com/ribbon-shapes](https://css-generators.com/ribbon-shapes/)