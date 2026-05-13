---
layout: layouts/post.njk
title: An Interactive Image Slider/Carousel
description: Using modern CSS to create a responsive image slider with speed control
date: 2026-05-13
tags: posts
---

I am combining the technique of making [an infinite marquee animation](/logo-marquee/) with [the speed control trick](/speed-control/) to create a responsive image slider with button controls. A CSS-only implementation that works with any number of images. Powered by modern CSS features such as `shape()`, `sibling-index()/count()`, `animation-composition`, etc.


{% image "./image.png", "CSS-only image slider with button controls" %}

```html
<div class="container">
  <img src="">
  <img src="">
  <!-- add as many images as you want -->
</div>
<div class="controls">
  <button aria-label="rewind"> ⏪︎ </button>
  <button aria-label="pause"> ⏸ </button>
  <button aria-label="fast forward"> ⏩︎ </button> 
</div>
```

```css
.container {
  --w: 250px; /* size of the image */
  --d: 15s;  /* animation duration */
  --n: 4;    /* number of visible images */
  
  display: flex;
}
img {
  width: var(--w);
  offset: shape(from calc(var(--w)/-2) 50%,hline by calc(sibling-count()*max(100%/var(--n),var(--w) + 10px)));
  animation: 
    x linear infinite var(--d) calc(-1*sibling-index()*var(--d)/sibling-count()),
    x linear infinite calc(var(--d)/2) paused,
    y linear infinite calc(var(--d)/4) paused;
  animation-composition: add;
}
.container:has(+ .controls button:nth-child(1):active) img {
  animation-play-state: running, paused, running;
}
.container:has(+ .controls button:nth-child(2):active) img {
  animation-play-state: paused;
}
.container:has(+ .controls button:nth-child(3):active) img {
  animation-play-state: running, running, paused;
}

@keyframes x {
  to {offset-distance: 100%}
}
@keyframes y {
  to {offset-distance: -100%}
}
```

<p class="codepen" data-height="500" data-pen-title="Interactive Image Slider" data-preview="true" data-default-tab="result" data-slug-hash="bNBwwmY" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bNBwwmY">
  Interactive Image Slider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

More details: [How to Control Infinite CSS Animations](https://frontendmasters.com/blog/how-to-control-infinite-css-animations-part-1-of-2/)