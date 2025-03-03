---
layout: layouts/post.njk
title: A fancy hover effect with rotating squares
description: Transform your image into little rotating squares with a fancy hover effect
date: 2023-04-26
tags: posts
---

Add a fancy hover effect to your image with a small code. Transform your image into little rotating squares!
* One element (the `<img>` tag)
* No pseudo-element
* Powered by CSS mask and @property


Pay attention to the support of [the @property](https://caniuse.com/mdn-css_at-rules_property).


{% image "./image.png", "Image with rotating squares" %}

```css
img {
  --n: 5; /* number of squares */

  --_g: #0000 var(--d,0%),#000 0;
  mask:
    linear-gradient(calc(  0deg + var(--r,0deg)),var(--_g)),
    linear-gradient(calc( 90deg + var(--r,0deg)),var(--_g)),
    linear-gradient(calc(-90deg + var(--r,0deg)),var(--_g)),
    linear-gradient(calc(180deg + var(--r,0deg)),var(--_g));
  mask-size: calc(100%/var(--n)) calc(100%/var(--n));
  mask-composite: intesect;
  outline: 100vmax solid #0009;
  outline-offset: -100vmax;
  transition: outline-color .5s;
  cursor: pointer;
}
img:hover {
  --d: 0.1%;
  --r: 90deg; 
  outline-color: #0000;
  transition: outline-color .3s .2s, --d .5s cubic-bezier(0,450,1,450),--r .5s linear;
}
```


<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="abRWELR" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/abRWELR">
  A fancy CSS-only hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


## Related links:
* [css-tricks.com/advanced-css-animation-using-cubic-bezier](https://css-tricks.com/advanced-css-animation-using-cubic-bezier/)
* [css-tricks.com/fancy-image-decorations-masks-and-advanced-hover-effects](https://css-tricks.com/fancy-image-decorations-masks-and-advanced-hover-effects/)