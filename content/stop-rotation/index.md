---
layout: layouts/post.njk
title: Smoothly stop a rotation on hover
description: A simple CSS trick to slowly stop a rotation on hover 
date: 2024-03-21
tags: posts
---

Make your rotation look more natural by smoothly stopping it on hover instead of an abrupt stop. No complex code is required!

The rotation will resume slowly on mouse-out as well.



```css
.box {
  animation: rotate 2s linear infinite;
  transition: 1s ease-out;
}
.box:hover {
  animation-play-state: paused;
  transform: rotate(.2turn);
}
@keyframes rotate {
  to {rotate: 1turn}
}
```
<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="XWQMPqY" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWQMPqY">
  Smooth stop the rotation on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

You can have the opposite effect by adjusting a few values. You smoothly start the rotation on hover.

The element will slowly stop on mouse-out as well.

```css
.box {
  animation: rotate 2s linear infinite paused;
  transition: 1s ease-out;
}
.box:hover {
  animation-play-state: running;
  transform: rotate(-.2turn);
}
@keyframes rotate {
  to {rotate: 1turn}
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="JjVNXxY" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JjVNXxY">
  Smoothly start the rotation on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>