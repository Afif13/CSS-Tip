---
layout: layouts/post.njk
title: Heart shape animation using outline
description: Turn your image into a heart with a cool animation
date: 2022-07-04
tags: posts
---

Add a beautiful animation to a [Heart shape](/image-heart-shape/) and reveal your best images 🥰 😍
* No extra element (only the `<img>` tag)
* No pseudo-element
* Less than 10 declarations


{% image "./heart.png", "An image with a heart shape" %}

```css
img {
  width: 250px;
  aspect-ratio: 1;
  object-fit: cover;
  mask-border: radial-gradient(#000 69%,#0000 70%) 84.5% fill/100%;
  clip-path: polygon(-41% 0,50% 91%, 141% 0);
  outline: 100vmax solid #ff3e60;
  outline-offset: -100vmax;
  transition: .7s;
}
img:hover {
  outline-color: #0000;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="WNzQQzQ" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/WNzQQzQ">
  CSS only heart hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
