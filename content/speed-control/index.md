---
layout: layouts/post.njk
title: Control the Speed of Infinite Animations
description: A simple code to easily control the speed of any infinite animation
date: 2026-05-06
tags: posts
---

Here is a simple code that lets you adjust the speed of your infinite animation on hover (or with other interactions). It relies on `animation-composition: add` that allows you to run the same animation twice with an additive effect. 

By pausing/running the second animation, you can make the overall animation faster, slower, or move it in the opposite direction. You can easily control this using one CSS variable.

```css
.box {
  --d: 5s; /* animation duration */
  --s: 2;  /* speed factor 
      [1  +infinite[ : move faster
      ]0  1[ : slow down 
      0: stop
      ]-infinity  0[ : move in the opposite direction 
  */
  --_a: animate linear infinite;
  animation: 
    var(--_a) var(--d),
    var(--_a) abs(var(--d)/(var(--s) - 1)) paused
    if(style(--s < 1):reverse;else: ;);
  animation-composition: add;
}
.box:hover {
  animation-play-state: running;
}
@keyframes animate {
  to {/* whatever you want to animate */}
}
```

Here is an example using an infinite rotation where each element has a different speed factor. Hover to see the result:

<p class="codepen" data-height="500" data-pen-title="Infinite Animation Speed Control" data-preview="true" data-default-tab="result" data-slug-hash="pvNvdVX" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/pvNvdVX">
  Infinite Animation Speed Control</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

The use of the inline condition `if()` is not well supported, so we can rely on the code below until better support is available:

```css
.box {
  --d: 5s; /* animation duration */
  --s: 2;  /* speed factor */
  
  animation: 
    init    linear infinite var(--d),
    control linear infinite abs(var(--d)/(var(--s) - 1)) paused;
  animation-composition: add;
}
.box:hover {
  animation-play-state: running;
}
@keyframes init {
  to {rotate: 1turn}
}
@keyframes control {
  to {rotate: calc(sign(var(--s) - 1)*1turn)}
}
```

All you have to do is change `rotate` with the property you want to animate.

Here is an example with an infinite marquee where I am animating the `offset-distance`:

<p class="codepen" data-height="550" data-pen-title="Infinite Marquee Speed Control" data-preview="true" data-default-tab="result" data-slug-hash="QwGjxPv" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwGjxPv">
  Infinite Marquee Speed Control</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Another example with a glowing border effect where I am animating a CSS variable:


<p class="codepen" data-height="400" data-pen-title="Glowing border Animation with hover effect" data-preview="true" data-default-tab="result" data-slug-hash="RNoNJLW" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RNoNJLW">
  Glowing border Animation with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
