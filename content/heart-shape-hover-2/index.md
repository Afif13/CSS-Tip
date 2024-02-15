---
layout: layouts/post.njk
title: Heart shape with a sliding hover effect II
description: A lovely animation to your heart shape image
date: 2024-02-15
tags: posts
---

Another variation of [the previous effect](/heart-shape-hover/) using the same code structure
* No extra element (only the `<img>` tag)
* No pseudo-elements


{% image "./image.png", "A CSS only heart shape" %}

```css
img {
  --s: 300px; /* image size */
  
  width: var(--s);
  aspect-ratio: 1;
  padding: calc(.09*var(--s)) calc(var(--s)/2 - var(--_p));
  box-sizing: border-box;
  object-fit: cover;
  border-image: 
    radial-gradient(#e5414e 69%,#0000 70%) 
    84.5%/calc(var(--s)/2)/0 var(--_p);
  clip-path: polygon(
    calc(-41% - var(--_p)) 0,
    calc(50%  - var(--_p)) 91%,
    calc(50%  + var(--_p)) 91%,
    calc(141% + var(--_p)) 0);
  transition: .5s;
  --_p: 0px;
}
img:hover {
  --_p: calc(var(--s)/2);
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="VwRqQZY" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/VwRqQZY">
  Heart shape image reveal  II ❤️</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>