---
layout: layouts/post.njk
title: Cut your image into pieces
description: Use CSS mask to cut your image into small pieces
date: 2022-01-02
tags: posts
---

Cut your image into small pieces using one CSS instruction.


{% image "./matrix.png", "A image cut into small pieces" %}


```css
img {
  --n: 10; /* number of rows */
  --m: 15; /* number of columns */
  --gap: 3px;
  mask:
    conic-gradient(from 90deg at var(--gap) var(--gap),#000 90deg,#0000 0) 
    calc(-1*var(--gap)) calc(-1*var(--gap))/
    calc((100% + var(--gap))/var(--m))
    calc((100% + var(--gap))/var(--n))
}
```


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="xxXWqym" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xxXWqym">
  cut image into small pieces</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>