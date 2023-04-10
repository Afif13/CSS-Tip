---
layout: layouts/post.njk
title: An infinite image slider
description: A minimal code to create an infinite image slider
date: 2022-09-16
tags: posts
---

Create an infinite image carousel using a few lines of code:
* Minimal HTML (`<img>`s inside a container)
* No duplicated images
* One simple animation
* Works with any number of images
* Optimized with Sass


```scss
$n:5; /* number of images*/

.gallery  {
  --d: 10s; /* duration */
  
  display: grid;
  overflow: hidden;
  width: 380px;
}
.gallery > img {
  grid-area: 1/1;
  width: 100%;
  aspect-ratio: 1.5;
  object-fit: cover;
  animation: r var(--d) linear infinite;
}
@for $i from 2 to ($n + 1) {
  .gallery > img:nth-child(#{$i}) {animation-delay: calc(#{(1 - $i)/$n}*var(--d))}
}
@keyframes r {
  #{100*($n - 1)/$n}% {transform: translate((1 - $n)*100%)}
  #{100*($n - 1)/$n + .01}% {transform: translate(100%)}
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="QWrdZLG" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QWrdZLG">
  CSS only infinite carousel (No duplicated images)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [verpex.com/blog/website-tips/how-to-create-an-infinite-image-slider-using-css](https://verpex.com/blog/website-tips/how-to-create-an-infinite-image-slider-using-css)