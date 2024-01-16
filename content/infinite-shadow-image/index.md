---
layout: layouts/post.njk
title: Infinite shadow for your images II
description: CSS trick to add a diagonal infinite shadow to your image 
date: 2023-12-06
tags: posts
---

Another variation of [the previous effect](/infinite-shadow/) where you can add a diagonal infinite shadow to your rounded image.
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Optimized with CSS variables


{% image "./image.png", "four images with a diagonal infinite shadow" %}

```css
img {
  --b: 8px; /* the border thickness*/
  --w: 200px; /* image width */
  --c: #A7DBD8;
  
  --_w: calc(0.1464*var(--w)); /* 0.1464 = (sqrt(2) - 1)/(2*sqrt(2)) */
  width: var(--w);
  border-radius: 50%; /* don't touch this, only rounded images */
  padding: var(--b);
  box-sizing: border-box;
  box-shadow: 0 0 0 var(--b) inset var(--c);
  border-image: conic-gradient(var(--c) 0 0) 1 0 0 1/
    calc(100% - var(--_w)) var(--_w) var(--_w) calc(100% - var(--_w))/
    999px 0 0 999px;
  clip-path: polygon(
    120.71% 50%,calc(120.71% - 999px) calc(50% - 999px),
    calc(50% - 999px) calc(120.71% - 999px),50% 120.71%);
}
```

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="mdvaeoq" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdvaeoq">
  Infinite image shadow II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related: [smashingmagazine.com/2024/01/css-border-image-property/](https://www.smashingmagazine.com/2024/01/css-border-image-property/)