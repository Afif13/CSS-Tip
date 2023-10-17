---
layout: layouts/post.njk
title: A Fancy Hover Effect For Your Avatar III
description: Create a stunning "Pop out" hover effect using modern CSS
date: 2023-09-13
tags: posts
---

Another fancy "Pop out" hover effect using modern CSS. The spiky variation of [the previous effect](/avatar-hover-effect-2)
* No extra element (only the `<img>` tag)
* No pseudo-element
* Powered by the future of CSS (mask, @property, Trigonometric functions and a lot of math)
* Optimized with Sass & CSS Variables

{% image "./image.png", "A pop out hover effect to image" %}

```scss
$n: 16; /* number of spikes */

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
  --r: 160px; /* control the size of the image */
  --p: 0.25;  /* control the size of the spikes (a uniteless value). It's a percentage of --r */
  --f: 1.3; /* the scale factor */
  --c: #E4844A; /* the main color */
  --bg: #E0E4CC; /* the color behind the element (the body background here). */
  
  --angle: atan(sin(180deg/#{$n})/(var(--p) - 1 + cos(180deg/#{$n})));
  width: calc(2*var(--r));
  aspect-ratio: 1;
  $m: ();
  @for $i from 0 through ($n - 1) {
    $m: append($m, 
         conic-gradient(
           from calc(90deg + 360deg*#{$i/$n} - var(--angle) + var(--a,0deg)) at  
           calc(50% + (50%*(1 - var(--p)) - var(--i,0px))*cos(360deg*#{$i/$n} + var(--a,0deg)))
           calc(50% + (50%*(1 - var(--p)) - var(--i,0px))*sin(360deg*#{$i/$n} + var(--a,0deg)))
           ,var(--bg) calc(2*var(--angle)),#0000 0),
        comma);
   }
  mask: 
    linear-gradient(#000 0 0) top/100% 50% no-repeat,
    linear-gradient(#000 0 0) exclude,
    $m;
  background: $m,var(--c);
  --_a: rotate linear infinite;
  animation: 
    var(--_a) 10s,
    var(--_a) 16s reverse;
  animation-composition: add;
  cursor: pointer;
  clip-path: circle(50%); /* better than border radius*/
  transition: --i .4s, scale .4s;
}
img:hover {
  --i: calc(var(--r)*(1 - var(--p))*(var(--f) - 1)/var(--f));
  scale: var(--f);
  animation-play-state: running, paused;
}
@keyframes rotate {
  to{--a:360deg}
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="mdawrLa" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdawrLa">
  Fancy Pop Out hover effect!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Detail: [www.smashingmagazine.com/2023/10/re-creating-pop-out-hover-effect-modern-css-part2](https://www.smashingmagazine.com/2023/10/re-creating-pop-out-hover-effect-modern-css-part2/)