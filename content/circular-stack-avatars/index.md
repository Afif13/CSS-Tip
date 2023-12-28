---
layout: layouts/post.njk
title: Circular list of stacked avatars
description: Create a list of stacked avatars with a nice hover effect
date: 2023-12-28
tags: posts
---

An [horizontal list](/horizontal-stack-avatars/) is good but a circular one is better 🤩

Another list of stacked avatars using the same code structure
* Minimal HTML (images inside a container)
* Works with any number of images
* Powered by modern CSS (CSS variables, mask, @property, and more)
* Optimized with Sass


{% image "./image.png", "CSS-only circular list of stacked avatars" %}

```scss
$n: 9; /* number of images*/

@property --h {
  syntax: "<length-percentage>";
  initial-value: 0%;
  inherits: true;
}
@property --m {
  syntax: "<length-percentage>";
  initial-value: 0%;
  inherits: true;
}
@property --t {
  syntax: "<length-percentage>";
  initial-value: 0%;
  inherits: true;
}

.container {
  --s: 150px; /* image size*/
  --o: 30px;  /* the overlap */
  --g: 12px;  /* the gap */ 
  
  --_d: calc(var(--s)/(2*sin(#{180/$n}deg)) - var(--o));
  display: grid;
  border-radius: 50%;
  width: calc(var(--s) + 2*var(--_d));
  aspect-ratio: 1;
  place-items: center;
  overflow: hidden;
  filter: drop-shadow(0 0 1px #000) drop-shadow(0 0 1px #000) drop-shadow(0 0 #000) drop-shadow(0 0 #000);
}
.container img {
  grid-area: 1/1;
  width: var(--s);
  aspect-ratio: 1;
  border-radius: 50%;
  transition: 1s;
  transition-property: --h ,--t,--m;
}
@for $i from 0 to $n {
  .container > img:nth-child(#{$i + 1}) {
    transform: 
      rotate(#{-360*$i/$n}deg) 
      translate(calc(var(--_d) - var(--t))) 
      rotate(#{ 360*$i/$n}deg);
  mask: padding-box radial-gradient(50% 50% at 
    calc(50% - (var(--_d) - var(--h))*cos(#{360*$i/$n}deg) 
             + (var(--_d) - var(--m))*cos(#{360*($i + 1)/$n}deg))  
    calc(50% + (var(--_d) - var(--h))*sin(#{360*$i/$n}deg) 
             - (var(--_d) - var(--m))*sin(#{360*($i + 1)/$n}deg)),
    #0000 calc(100% + var(--g)),#000 calc(101% + var(--g)))
  }
}
img:hover {
  --t: var(--_d);
  --h: var(--_d);
  border: var(--_d) solid #0000;
  z-index: -1;
}
img:has(+ img:hover),
.container:has(img:first-child:hover) img:last-child{
  --m: var(--_d);
}
```

<p class="codepen" data-height="650" data-default-tab="result" data-slug-hash="yLwyWmp" data-preview="true" data-user="t_afif" style="height: 650px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLwyWmp">
  Stacked Avatars with hover effect II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>