---
layout: layouts/post.njk
title: Overlapping border on images with hover effect
description: Add an overlapping border to your image with cool hover effect
date: 2023-07-06
tags: posts
---

Add an overlapping border to your image with a nice hover effect
* No extra element (only the `<img>` tag)
* No pseudo-element
* 10 CSS declarations
* Optimized with CSS variables

{% image "./image.png", "images with overlapping border" %}

```css
img {
  --c: #F9CDAD; /* the main color */
  --b: 8px; /* thickness of the border */
  --o: 25px; /* control the offset */
  
  width: 200px; /* the image size */
  --_p: calc(2*var(--o) + var(--b));
  padding: var(--_p) var(--_p) 0 0;
  outline: var(--b) solid var(--c);
  outline-offset: calc(var(--o) - var(--_p));
  transition: .4s;
}
img:hover {
  padding: calc(var(--_p)/2);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="PoxKmgX" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PoxKmgX">
  Overlapping border on image (with hover effect)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [verpex.com/blog/website-tips/css-effects-on-images-ii](https://verpex.com/blog/website-tips/css-effects-on-images-ii)