---
layout: layouts/post.njk
title: A Fancy Hover Effect For Your Avatar II
description: Create a stunning "Pop out" hover effect using modern CSS
date: 2023-08-14
tags: posts
---

Add a fancy "Pop out" hover effect to your avatar using modern CSS. Another variation of [the previous effect](/avatar-hover-effect)
* No extra element (only the `<img>` tag)
* No pseudo-element
* Powered by the future of CSS (mask, @property, Trigonometric functions and a lot of math)
* Optimized with Sass & CSS Variables

{% image "./image.png", "A pop out hover effect to image" %}

```scss
$n: 15; /* number of small circles */

@property --a {
  syntax: "<angle>";
  initial-value: 0deg;
  inherits: true;
}
@property --i {
  syntax: "<length>";
  initial-value: 0px;
  inherits: true;
}

img {
  --r: 50px; /* control the small circles radius and the main size */
  --f: 1.7;  /* control the scale factor, between 1.2 and 2 you get nice result */
  --c: #E4844A;
  
  width: calc(var(--r)*(1 + 1/tan(180deg/#{$n})));
  aspect-ratio: 1;
  border-radius: 50%;
  $m: ();
  @for $i from 1 through ($n) {
    $m: append($m, 
         radial-gradient(var(--c) 70%,#0000 72%) no-repeat
          calc(50% + (50% - var(--i,0px))*cos(360deg*#{$i/$n} + var(--a,0deg))) 
          calc(50% + (50% - var(--i,0px))*sin(360deg*#{$i/$n} + var(--a,0deg)))/
          var(--r) var(--r), 
        comma);
   }
  --_m: 
    radial-gradient(var(--c) calc(72% - var(--r)/2 - var(--i,0px)),#0000 0) no-repeat,
    #{$m};
  mask: 
    linear-gradient(#000 0 0) top/100% 50% no-repeat,
    var(--_m);
  background: var(--_m);
  --_a: rotate linear infinite;
  animation: 
    var(--_a) 10s,
    var(--_a) 16s reverse;
  animation-composition: add;
  cursor: pointer;
  transition: --i .4s, scale .4s;
}
img:hover {
  --i: calc(var(--r)/var(--f));
  scale: calc((1 + 1/tan(180deg/#{$n}))/(1 - 2/var(--f) + 1/tan(180deg/#{$n})));
  animation-play-state: running, paused;
}
@keyframes rotate {
  to{--a:360deg}
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="qBQzrwq" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBQzrwq">
  Fancy Pop Out hover effect!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Detail: [www.smashingmagazine.com/2023/09/re-creating-pop-out-hover-effect-css-part1](https://www.smashingmagazine.com/2023/09/re-creating-pop-out-hover-effect-css-part1/)