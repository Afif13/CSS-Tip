---
layout: layouts/post.njk
title: A single-element volume control component 
description: Use modern CSS to tranform a native input element into a volume control component
date: 2025-02-04
tags: posts
---

Similar to [the star rating component](/star-rating/), I am creating a volume control component using the native range slider and zero JavaScript. No extra element is used and you can control the number of bars by simply adjusting the `max` attribute.

{% image "./image.png", "CSS-only volume control component" %}

```html
<input type="range" min="1" max="5">
```

```css
input[type=range] {
  --s: 50px; /* the size of the bar (including the gap) */
  --g: 30%;  /* the gap (percentage of the above size) */
  
  --_n: attr(max type(<integer>)); /* update max to control the number of bars */
  aspect-ratio: 3/2; /* you can update this as well */
  width: calc(var(--_n)*var(--s));
  padding-inline: calc(var(--s)/2);
  box-sizing: border-box;
  mask:
    linear-gradient(90deg,#0000 calc(var(--g)/2),#000 0 calc(100% - var(--g)/2),#0000 0) 
     0/var(--s) intersect,
    linear-gradient(to top left,#000 50%,#0000 0),
    repeating-conic-gradient(#000 0 25%,#0000 0 50%)
     0 100%/calc(2*var(--s)) calc(200%/var(--_n));
  clip-path: polygon(100% calc(-100%/var(--_n)),100% 100%,calc(-100%/var(--_n)) 100%);
  appearance: none;
}
input[type="range" i]::-webkit-slider-thumb{
  width: 1px;
  border-image: 
    conic-gradient(at calc(50% + var(--s)/2),#D9CEB2 50%,#3FB8AF 0)
    fill 0//400px calc(var(--_n)*var(--s));
  appearance: none;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="mybYpPW" data-pen-title="CSS-only volume control (click to update!)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mybYpPW">
  CSS-only volume control (click to update!)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>