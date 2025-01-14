---
layout: layouts/post.njk
title: Smoothly stop an infinite rotation
description: Using modern CSS to stop an infinite rotation on hover
date: 2025-01-14
tags: posts
---

After [the previous effect](/stop-rotation/), here is a different way to stop an infinite rotation on hover. This time, the element will smoothly return to its initial position and the rotation will resume when you unhover.


```css
@property --a {
  syntax: "<angle>";
  inherits: false;
  initial-value: -100turn; /* not really infinite but you get the idea */
}
@property --i {
  syntax: "<number>";
  inherits: false;
  initial-value: 1; 
}
.box {
  --t: 1turn; /* control the modulo (the smallest angle after which you get back to the same visual) */
  --d: .8s;   /* the transition on hover */
  
  rotate: calc(mod(var(--a),var(--t))*var(--i));
  transition: --i 0s,--a 200s linear;
  @starting-style {
    --a: 0turn;
  }
}
.box:hover {
  --i: 0;
  --a: 0turn;
  transition: --i var(--d) ease-out,--a 0s var(--d);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="azoGVPe" data-pen-title="Stop infinite rotation on hover" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/azoGVPe">
  Stop infinite rotation on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Here is another demo using the same technique. Hover the image to stop the animation smoothly.


<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="PwYeOrK" data-pen-title="Glowing border with infinite animation (hover for a smooth stop)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PwYeOrK">
  Glowing border with infinite animation (hover for a smooth stop)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>