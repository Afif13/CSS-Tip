---
layout: layouts/post.njk
title: Split and assemble an image using CSS mask
description: A few lines of code to create a fancy reveal animation for images
date: 2025-03-18
tags: posts
---

Split an image into pieces using the `mask` property, then show it fully on hover. A single-element implementation using less than 10 CSS declarations.


{% image "./image.png", "Assemble a broken image using CSS" %}


```css
img {
  --g: 15px; /* control the gap */
  
  width: 280px;
  aspect-ratio: 1;
  box-sizing: border-box;
  --_g: var(--g)/calc(50% - var(--g)) calc(50% - var(--g)) 
    no-repeat conic-gradient(#000 0 0);
  mask: 
    left   var(--_i,) top    var(--_g),
    bottom var(--_i,) left   var(--_g),
    top    var(--_i,) right  var(--_g),
    right  var(--_i,) bottom var(--_g);
  transition: .3s linear;
}
img:hover {
  --_i: var(--g);
  padding: var(--g);
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="yyLvRqW" data-pen-title="Image assembly hover effect" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyLvRqW">
  Image assembly hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another simpler version without the moving effect:

```css
img {
  --_g: 10%/45% 45% no-repeat conic-gradient(#000 0 0);
  mask: 
    left   var(--_i,) top    var(--_g),
    bottom var(--_i,) left   var(--_g),
    top    var(--_i,) right  var(--_g),
    right  var(--_i,) bottom var(--_g);
  transition: .3s linear;
}
img:hover {
  --_i: 10%;
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="qBpyWgK" data-pen-title="Image mask hover effect" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBpyWgK">
  Image mask hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>