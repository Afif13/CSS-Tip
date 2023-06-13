---
layout: layouts/post.njk
title: Slow down a rotation on hover
description: A simple trick to reduce the speed of your rotating element 
date: 2023-06-13
tags: posts
---

Did you ever wanted to slow down a rotating element on mouse hover? You can easily do it with a simple code:
* No extra element 
* No pseudo-element
* One animation
* Easy to control with CSS variables


```css
.box {
  --d: 5s; /* animation duration */
  --s: 0.5; /* speed factor 
          0   : nothing happens
         [0 1]: decrease the speed
            1 : stops the animation
[1 +infinity[ : move in the opposite direction
  */
  --_a: r linear infinite;
  animation: 
    var(--_a) var(--d),
    var(--_a) calc(var(--d)/var(--s)) 
    reverse paused;
  animation-composition: add;
}
.box:hover {
  animation-play-state: running;
}
```

There is a fallback version for browsers that don't support `animation-composition`. It is also an interesting way with a simple code.


<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="vYQNLoe" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/vYQNLoe">
  Hover to slow down the animation</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

