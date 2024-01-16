---
layout: layouts/post.njk
title: Infinite stripes shadow for your images 
description: Add an infinite shadow with stripes to your image 
date: 2023-12-08
tags: posts
---

Another variation of [the previous effect](/infinite-shadow-image/) with infinite stripes
* No extra element (only the image tag)
* No pseudo-elements
* Optimized with CSS variables


{% image "./image.png", "CSS infinite stripes shadow" %}

```css
img {
  --b: 8px; /* the border thickness*/
  --w: 216px; /* image width */
  --c: #A7DBD8;
  
  
  --_w: calc(0.1464*var(--w));
  width: var(--w);
  border-radius: 50%; /* don't touch this, only rounded images */
  padding: var(--b);
  box-shadow: 0 0 0 var(--b) inset var(--c);
  border-image:
    repeating-radial-gradient( 
      at calc(100% - var(--w)/2 + var(--_w)) calc(100% - var(--w)/2 + var(--_w)),
      var(--c) 0,#0000 1px var(--b),var(--c) calc(var(--b) + 1px) calc(var(--b)*2)
    ) 9999 0 0 9999/
    calc(100% - var(--_w)) var(--_w) var(--_w) calc(100% - var(--_w))/
    999px 0 0 999px;
  clip-path: 
    polygon(
      120.71% 50%,calc(120.71% - 999px) calc(50% - 999px),
      calc(50% - 999px) calc(120.71% - 999px),50% 120.71%);
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="yLZwLKj" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLZwLKj">
  Infinite image stripes shadow </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related: [smashingmagazine.com/2024/01/css-border-image-property/](https://www.smashingmagazine.com/2024/01/css-border-image-property/)