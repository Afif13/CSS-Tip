---
layout: layouts/post.njk
title: CSS-only folded ribbon
description: Use clip-path to create fanct folded ribbon
date: 2022-02-07
tags: posts
---

Create a cool Ribbon using one element and a few lines of code.
* Easy to update using CSS variables
* No hard-coded values
* Works with any text content
* Works with multi-lines of text

{% image "./ribbon.png", "A CSS ribbon" %}

```css
.ribbon {
  --f: 10px; /* control the folded part*/
  --r: 15px; /* control the ribbon shape */
  
  position: absolute;
  top: 10px;
  background: #BD1550;
  border-bottom: var(--f) solid #0005;
}
.left {
  left: calc(-1*var(--f));
  border-right: var(--r) solid #0000;
  clip-path: 
    polygon(100% 0,0 0,0 calc(100% - var(--f)),var(--f) 100%,
      var(--f) calc(100% - var(--f)),100% calc(100% - var(--f)),
      calc(100% - var(--r)) calc(50% - var(--f)/2));
}
.right {
  right: calc(-1*var(--f));
  border-left: var(--r) solid #0000;
  clip-path: 
    polygon(0 0,100% 0,100% calc(100% - var(--f)),calc(100% - var(--f)) 100%,
      calc(100% - var(--f)) calc(100% - var(--f)),0 calc(100% - var(--f)),
      var(--r) calc(50% - var(--f)/2));
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="gOXLdMR" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gOXLdMR">
  CSS only ribbon</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More Ribbon Shapes: [css-generators.com/ribbon-shapes](https://css-generators.com/ribbon-shapes/)