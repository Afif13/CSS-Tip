---
layout: layouts/post.njk
title: Turn your image into a heart
description: Create a CSS heart shape using any image
date: 2022-07-01
tags: posts
---

Turn your favorite image into a [Heart 💖](https://css-shape.com/heart/) using a few lines of code 
* No extra element (only the `<img>` tag)
* No pseudo-element
* Only two CSS declarations


{% image "./heart.png", "An image with a heart shape" %}

```css
img {
  mask-border: radial-gradient(#000 69%,#0000 70%) 84.5%/50%;
  clip-path: polygon(-41% 0,50% 91%, 141% 0);
}
```

For better support we can rely on `mask`

```css
img {
  mask:
   radial-gradient(at 70% 31%,#000 29%,#0000 30%),
   radial-gradient(at 30% 31%,#000 29%,#0000 30%),
   linear-gradient(#000 0 0) bottom/100% 50% no-repeat;
  clip-path: polygon(-41% 0,50% 91%, 141% 0);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="PoRwjPM" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PoRwjPM">
  CSS only heart images</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related Article: [verpex.com/blog/website-tips/css-shapes-the-heart](https://verpex.com/blog/website-tips/css-shapes-the-heart)