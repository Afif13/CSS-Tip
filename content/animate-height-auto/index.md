---
layout: layouts/post.njk
title: Animate to height/width auto (without hacks)
description: A new CSS feature to easily animate to height/width auto with no complex code
date: 2024-09-25
tags: posts
---

Only three lines of code and you have a smooth transition to `height: auto`

```css
& {
  interpolate-size: allow-keywords;
}
p {
  transition: 1s;
}
p:not(:hover) {
  height: 5lh;
}
```

The `interpolate-size: allow-keywords` is doing all the magic. Read [Animate to height: auto; (and other intrinsic sizing keywords) in CSS](https://developer.chrome.com/docs/css-ui/animate-to-height-auto) for more detail.

Try the below using the lastest version of chrome:

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="BaXyWbd" data-pen-title="Animating to height: auto" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/BaXyWbd">
  Animating to height: auto</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>