---
layout: layouts/post.njk
title: Extend the background to the edge of the screen
description: Use a border-image trick to create an overflowing background
date: 2022-06-09
tags: posts
---

Extend the background of an element outside of its container to cover the full screen width
* No extra element
* No pseudo-element
* No overflow issue
* Only one CSS declaration

{% image "./background.png", "An overflowing background" %}

```css
.full-background {
  border-image: conic-gradient(pink 0 0) fill 0//0 100vw;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="oNEaqQX" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/oNEaqQX">
  Full screen background color</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another idea more versbose using `box-shadow`

```css
.full-background {
  --c: pink;
  background: var(--c);
  /* a big box-shadow */
  box-shadow: 0 0 0 100vw var(--c);
  /* clip only the top and bottom part of it */
  clip-path: inset(0 -100vw);
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="LYQgPgM" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LYQgPgM">
  Full screen background color</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>