---
layout: layouts/post.njk
title: The gotcha of align-content with block elements
description: The new align-content won't center your content like you may expect
date: 2024-03-11
tags: posts
---

Everyone is excited about the new `align-content` that works with block-level elements, but pay attention when you want to center elements such as `<img>`, `<iframe>`, `<canvas>`, `<video>`, etc.

⚠️ They won't get centered ⚠️

They will look centered but in reality, they are not and this is not a bug!

{% image "./image.png", "Illustrating the effect of align-content on image inside block level elements: the image is not perfectly centered" %}

Images and similar inline-level elements have that strange white space under them due to the default baseline alignment, and that space is preserved when using `align-content` because we align the "whole content"

So don't forget to get rid of that space using `vertical-align: top`

{% image "./image.png", "Adding vertical-align: top to the image to have a perfect centering alignment" %}

That space may look small but it can make a difference especially if you use a big `font-size`. 

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="bGJpKGX" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bGJpKGX">
  align-content with block elements </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>