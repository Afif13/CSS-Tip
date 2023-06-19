---
layout: layouts/post.njk
title: 3D shine animation with a hover effect
description: a fancy 3D animation to your image with a cool hover effect
date: 2023-06-19
tags: posts
---

Add a fancy 3D animation to your image with a cool hover effect
* No extra element (only the `<img>` tag)
* No pseudo-element
* Optimized with CSS variables


{% image "./image.png", "A 3D shine animation on image" %}

```css
img {
  --c: #bec1c9; /* the main coloration of the rotating gradient */
  width: 250px; /* the size of the image*/
  aspect-ratio: 1;
  border-radius: 25px;
  border: 4px solid #0000; /* the thickness for the rotating gradient */
  padding: 10px; /* the gap */
  background: 
    conic-gradient(from var(--a),
       #0000 calc(30% - var(--p)),
       var(--c) calc(50% - var(--p)) calc(50% + var(--p)),
       #0000 calc(70% + var(--p))) border-box;
  --g: linear-gradient(#000 0 0);
  mask: 
    var(--g),var(--g) padding-box,
    conic-gradient(from var(--a),
       #000d calc(30% - var(--p)),
       #000  calc(50% - var(--p)) calc(50% + var(--p)),
       #000d calc(70% + var(--p))) content-box;
  mask-composite: exclude;
  --_t: perspective(450px); /* the bigger, the better */
  animation: 4s linear infinite;
  animation-name: a,r;
  transition: --p .5s,--r .4s;
}
img:hover {
  --p: 50%;
  --r: 0deg;
  animation-play-state: paused;
}
@keyframes a {
  to {--a: 405deg}
}
@keyframes r{
  0%,
  100%  {transform: var(--_t) rotate3d( 1, 1,0,var(--r))}
  12.5% {transform: var(--_t) rotate3d( 0, 1,0,var(--r))}
  25%   {transform: var(--_t) rotate3d(-1, 1,0,var(--r))}
  37.5% {transform: var(--_t) rotate3d(-1, 0,0,var(--r))}
  50%   {transform: var(--_t) rotate3d(-1,-1,0,var(--r))}
  62.5% {transform: var(--_t) rotate3d( 0,-1,0,var(--r))}
  75%   {transform: var(--_t) rotate3d( 1,-1,0,var(--r))}
  87.5% {transform: var(--_t) rotate3d( 1, 0,0,var(--r))}
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="gOQMMMj" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gOQMMMj">
  3D shine animation with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


