---
layout: layouts/post.njk
title: A fancy title divider I
description: Use background and border-image to create a fancy title divider
date: 2022-08-25
tags: posts
---

Turn your titles into a fancy divider using few lines of code
* No extra element
* No pseudo element
* No overflow issue
* Easy to update using CSS variables


{% image "./title-divider.png", "A title with a fancy decoration" %}

```css
.fancy {
  --b: 6px;   /* control the border thickness */
  --w: 80px;  /* control the width of the line*/
  --g: 15px;  /* control the gap */
  --c: #0B486B;
 
  border: 1px solid;
  background: 
    conic-gradient(from   45deg at left ,var(--c) 25%,#0000 0) 0,
    conic-gradient(from -135deg at right,var(--c) 25%,#0000 0) 100%;
  background-size: 51% 100%;
  background-origin: border-box;
  background-repeat: no-repeat;
  border-image: 
     linear-gradient(
       #0000      calc(50% - var(--b)/2),
       var(--c) 0 calc(50% + var(--b)/2),
       #0000    0) 
    1/0 var(--w)/calc(var(--w) + var(--g));
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="VwXOmjW" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/VwXOmjW">
  Fancy title divider with one element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

