---
layout: layouts/post.njk
title: Avatar with status indicator
description: A few lines of code to add a status indicator to any image
date: 2024-04-30
tags: posts
---

Use modern CSS to add that little status indicator to your avatar using less than 10 CSS declarations and without extra elements.
* Only the `<img>` tag
* No pseudo-elements
* Transparent gap
* Optimized with CSS variables
* Subtle animation on hover

{% image "./image.png", "CSS-only avatar with status indicator" %}

```css
@property --s {
  syntax: "<length>";
  initial-value: 0px;
  inherits: true;
}
img {
  --w: 170px; /* the image size */
  --s: 12px;  /* control the indicator size */
  --g: 3px;   /* control the gap (+ a default gap) */
  
  width: var(--w);
  aspect-ratio: 1;
  padding: 0 calc(var(--w)/sqrt(2)) calc(var(--w)/sqrt(2)) 0;
  margin: 0 calc(-1*var(--w)/sqrt(2)) calc(-1*var(--w)/sqrt(2)) 0;
  outline: var(--s) solid #B90504;
  outline-offset: -9e9q;
  mask: 
    radial-gradient(#000 calc(var(--s) - 1px),#0000 var(--s)),
    radial-gradient(#000 70%,#0000 71%) 0 0/var(--w) var(--w) subtract,
    radial-gradient(
      #000  calc(sqrt(2)*var(--s) + var(--g)),
      #0000 calc(sqrt(2)*var(--s) + var(--g) + 1px));
  /* clip-path is only needed to reduce the mouse interaction area */
  clip-path: circle(calc(var(--w)/2 + var(--s)) at calc(var(--w)/2) calc(var(--w)/2));
  transition: --s .5s;
}
img:hover {
  --s: 16px;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="yLrWeQP" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLrWeQP">
  Status indicator using only an image element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>