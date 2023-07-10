---
layout: layouts/post.njk
title: 3D parallax effect on images
description: A fancy 3D hover effect to your image with a simple code
date: 2023-05-16
tags: posts
---

Add a fancy 3D effect to your image with a simple code
* No extra element (only the `<img>` tag)
* No pseudo-element
* No JavaScript
* Perfect 3D illusion on hover 🤩


{% image "./image.png", "A 3D effect to your image" %}

```css
img {
  --f: .1; /* the parallax factor (the smaller the better) */
  --r: 10px; /* radius */
  
  --_f: calc(100%*var(--f)/(1 + var(--f)));
  --_a: calc(90deg*var(--f));
  width: 250px; /* the image size */
  aspect-ratio: calc(1 + var(--f));
  object-fit: cover;
  clip-path: inset(0 var(--_f) 0 0 round var(--r));
  transform: perspective(400px) var(--_t,rotateY(var(--_a)));
}
img:hover {
  clip-path: inset(0 0 0 var(--_f) round var(--r));
  --_t:translateX(calc(-1*var(--_f))) rotateY(calc(-1*var(--_a)))
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="qBJyXNy" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBJyXNy">
  3D parallax effect on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [smashingmagazine.com/2023/07/shines-perspective-rotations-css-3d-effects-images](https://www.smashingmagazine.com/2023/07/shines-perspective-rotations-css-3d-effects-images/)