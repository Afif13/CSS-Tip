---
layout: layouts/post.njk
title: Corner-only borders with hover effect
description: A simple trick to add corner-only borders to your image 
date: 2023-07-13
tags: posts
---

Add corner-only borders to your images with a nice hover effect
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 10 CSS declarations
* Only 2 gradients

{% image "./image.png", "Images with corner-only border" %}

```css
img {
  --s: 50px; /* the size on the corner */
  --t: 5px;  /* the thickness of the border */
  --g: 20px; /* the gap between the border and image */
  
  padding: calc(var(--g) + var(--t));
  outline: var(--t) solid #B38184; /* the color here */
  outline-offset: calc(-1*var(--t));
  -webkit-mask:
    conic-gradient(at var(--s) var(--s),#0000 75%,#000 0)
    0 0/calc(100% - var(--s)) calc(100% - var(--s)),
    linear-gradient(#000 0 0) content-box;
  transition: .4s;
}
img:hover {
  outline-offset: calc(var(--g)/-1);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="zYMpXbW" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYMpXbW">
  Corner-only borders with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [verpex.com/blog/website-tips/css-effects-on-images-ii](https://verpex.com/blog/website-tips/css-effects-on-images-ii)
