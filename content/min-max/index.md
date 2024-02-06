---
layout: layouts/post.njk
title: When to use the min() or max() function
description: a quick trick to know when to use min() or max()
date: 2024-02-06
tags: posts
---

`min()` or `max()`? You always struggle to know which one to use and you end up trying both until one of them works.

💡 Here is a figure to help you decide when to use them

You start with `clamp()` then: 
* when you remove max, you use `max()`
* when you remove min, you use `min()`


{% image "./image.png", "A 3D shine animation on image" %}

If you want to set a `max-width` to your element then it's `min()`

`width: clamp(min,100%,max)` ➞ `width: min(100%, max)`

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="KKEeLpp" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKEeLpp">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

If you want to set a min value for `font-size` then it's `max()`

`font-size: clamp(min,5vw,max)` ➞ `font-size: max(min, 5vw)`

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="KKEeLzd" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKEeLzd">
  min font-size using max()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>