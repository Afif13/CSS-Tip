---
layout: layouts/post.njk
title: 3D effect on images
description: a clip-path trick to apply a 3D effect on images
date: 2022-02-11
tags: posts
---

Add a 3D effect to your images with a few lines of code:
* No extra element (only the `<img>` tag)
* No pseudo element
* No duplicated image
* A cool animation on hover

{% image "./d.png", "Images with 3D effect" %}

```css
img {
  /* adjust the below to control the 3D effect */
  --x: 10px;
  --y: 20px;
  transform: perspective(1000px) rotateX(var(--_a,40deg));
  /* */
  
  clip-path: polygon(       
     var(--y)              var(--y),       
     calc(100% - var(--y)) var(--y),       
     calc(100% - var(--y)) calc(100% - var(--y)),       
     calc(100% - var(--y) - var(--x)) var(--_c,100%),       
     calc(var(--x) + var(--y))        var(--_c,100%),      
     var(--y)        calc(100% - var(--y))       
     );
  outline: var(--y) solid rgba(0,0,0,0.4);
  outline-offset: calc(-1*var(--y));
  padding: var(--y) var(--y) 0 var(--y);
  transition: 1s;
}
.box:hover img {
  --_a: 0deg;
  --_c: calc(100% - var(--y));
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="BamZomE" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/BamZomE">
  CSS only 3D effect image</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [dev.to/afif/3d-image-with-one-element-1c87](https://dev.to/afif/3d-image-with-one-element-1c87)