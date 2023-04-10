---
layout: layouts/post.njk
title: Turn your image into a heart
description: Create a CSS heart shape using any image
date: 2022-07-01
tags: posts
---

Turn your favorite image into a Heart 💖 using a few lines of code 
* No extra element (only the `<img>` tag)
* No pseudo-element
* Only two CSS declarations


{% image "./heart.png", "An image with a heart shape" %}

```css
img {
  mask-border: radial-gradient(#000 69%,#0000 70%) 84.5% fill/100%;
  clip-path: polygon(-41% 0,50% 91%, 141% 0);
}
```

For better support we can rely on `mask`

```css
img {
  mask:
   radial-gradient(circle at 60% 63%,#000 64%,#0000 65%) top left /50% 50% no-repeat,
   radial-gradient(circle at 40% 63%,#000 64%,#0000 65%) top right/50% 50% no-repeat,
   linear-gradient(#000 0 0) bottom/100% 50% no-repeat;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="PoRwjPM" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PoRwjPM">
  CSS only heart images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
