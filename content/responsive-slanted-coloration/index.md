---
layout: layouts/post.njk
title: Responsive full-screen slanted coloration
description: three CSS proeprties for a fancy full width responsive coloration
date: 2024-02-07
tags: posts
---

Use modern CSS to:
* Set a max-width
* Center an element
* Set a minimum margin
* Add a full-width slanted coloration
* Make the slant effect responsive

All of this, using only 3 properties and easy to control with CSS variables 

{% image "./image.png", "max-width section with a full screen responsive slanted coloration" %}

```css
section {
  --w: 800px; /* max-wdith */
  --s: 2rem;  /* control the slanted effect */
  --c: pink;
  
  margin: var(--s,0) max(1rem,50% - var(--w)/2);
  border-image: fill 0//99vw conic-gradient(var(--c) 0 0);
  --_s: clamp(0px,(100vw - var(--w))*999,var(--s)/2);
  clip-path: margin-box
    polygon(
      0    calc(var(--s)/2 + var(--_s)),
      100% calc(var(--s)/2 - var(--_s)),
      100% calc(100% - var(--s)/2 - var(--_s)),
      0    calc(100% - var(--s)/2 + var(--_s))
    );
}
```

Resize the screen to see the responsive part of the slant effect

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="jOJpZZb" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jOJpZZb">
  Slanted responsive coloration</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>