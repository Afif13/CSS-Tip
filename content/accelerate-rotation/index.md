---
layout: layouts/post.njk
title: Accelerate a rotation on hover
description: A simple CSS trick to speed up of your rotating element 
date: 2024-03-19
tags: posts
---

Do you want to accelerate the rotation of your element on hover? Here is a simple CSS trick using `animation-composition` and a few lines of code
* No extra element 
* No pseudo-element
* One animation


```css
.box {
  --_a: rotate 5s linear infinite;
  animation: var(--_a),var(--_a) paused;
  animation-composition: add;
}
.box:hover {
  animation-play-state: running;
}
@keyframes rotate {
  to {rotate: 1turn}
}
```
<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="ZEZLRXd" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEZLRXd">
  Accelerate a rotation on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

The same trick can be used [to slow down the rotation](/slow-down-rotation/)