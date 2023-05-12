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
  --t: 10px; /* the top offset */
  
  position: absolute;
  inset: var(--t) calc(-1*var(--f)) auto auto;
  padding: 0 10px 0 calc(10px + var(--r));
  clip-path: 
    polygon(0 0,100% 0,100% calc(100% - var(--f)),calc(100% - var(--f)) 100%,
      calc(100% - var(--f)) calc(100% - var(--f)),0 calc(100% - var(--f)),
      var(--r) calc(50% - var(--f)/2));
  background: #BD1550; /* the main color */
  border-bottom: var(--f) solid #0005;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="gOXLdMR" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gOXLdMR">
  CSS only ribbon</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [www.freecodecamp.org/news/make-a-css-only-ribbon](https://www.freecodecamp.org/news/make-a-css-only-ribbon/)

### More Ribbons

* [A Folded Ribbon To The Corner](/folded-ribbon/)
* [A CSS-only Ribbon](/css-ribbon-2/)