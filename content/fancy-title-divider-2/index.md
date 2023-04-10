---
layout: layouts/post.njk
title: A fancy title divider II
description: Use clip-path and border-image to create a fancy title divider
date: 2022-08-26
tags: posts
---

After [the previous one](/fancy-title-divider/), here is another fancy design for your title
* No extra element
* No pseudo element
* No overflow issue
* Less than 15 CSS declarations
* Optimized with CSS variables


{% image "./title-divider.png", "A title with a fancy decoration" %}

```css
.fancy {
  --b: 5px;   /* control the border thickness */
  --w: 100px; /* control the width of the line*/
  --h: 1.6em; /* control the height of the element */
  --c: #0B486B;
 
  padding: 0 calc(2*var(--h)/3);
  line-height: var(--h);
  clip-path: 
    polygon(
     calc(var(--h)/2) 0,100vw 0,
     100vw var(--b),100%  var(--b),
     calc(100% - var(--h)/2) 100%,-100vw 100%,
    -100vw calc(100% - var(--b)),0 calc(100% - var(--b))
    );
  border-image: var(--_g,linear-gradient(var(--c) 0 0)) fill 0//0 var(--w);
}
.dash {
  background: var(--c);
  --_g: repeating-linear-gradient(90deg,var(--c) 0 10px,#0000 0 15px);
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zYWQmyo" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYWQmyo">
  Fancy title divider with one element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

