---
layout: layouts/post.njk
title: Transparent inner border for images
description: A simple code to add a fancy transparent inner border to image elements
date: 2025-03-06
tags: posts
---

Cut a border from the inside of an image using the `mask` property and two gradients.

{% image "./image.png", "CSS-only inverted radius shape" %}

```css
img {
  --o: 20px; /* offset of the border*/
  --b: 5px;  /* border thickness */
  
  mask:
    conic-gradient(#000 0 0) no-repeat 50%/
     calc(100% - 2*(var(--o) + var(--b))) 
     calc(100% - 2*(var(--o) + var(--b))),
    conic-gradient(from 90deg at var(--o) var(--o),#0000 25%,#000 0)
     0 0/calc(100% - var(--o)) calc(100% - var(--o));
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="YPzVmmd" data-pen-title="Transparent inner border for images" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/YPzVmmd">
  Transparent inner border for images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Here is another demo with a hover effect

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="jOzzzLL" data-pen-title="Transparent inner border with hover effect" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jOzzzLL">
  Transparent inner border with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>