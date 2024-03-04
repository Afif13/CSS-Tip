---
layout: layouts/post.njk
title: CSS Functions that work without arguments
description: Some functions in CSS don't require arguments and it can be helpful
date: 2024-02-28
tags: posts
---

Do you know that some CSS functions can be used without arguments?

This is the case with `circle()` and `ellipse()` of `clip-path`. No need to provide any argument and they will, by default, round your element. `circle()` is a particular case of the `ellipse()` and is useful with square elements.

{% image "./image2.png", "clip-path circle and ellipse" %}

The browser will default `circle()` to `circle(closest-side at center)` and `ellipse()` to `ellipse(closest-side closest-side at center)`


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="wvZwapN" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wvZwapN">
  clip-path: circle()/ellipse()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

The filter functions can also be used without arguments. Most of them have no effect on the element except for `invert()`, `grayscale()`, and `sepia()`

{% image "./image.png", "CSS filter function (sepia, grayscale and invert)" %}

You can invert the colors of your image, turn it into black & white, or make it sepia without the need to remember the values you have to provide to each function.

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="XWQrPmP" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWQrPmP">
  filter: invert()/grayscale()/sepia()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>