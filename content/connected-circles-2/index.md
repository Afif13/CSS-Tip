---
layout: layouts/post.njk
title: Connecting Circles With Anchor Positioning II
description: Connect circles with arrows and show their distance using modern CSS
date: 2026-01-08
tags: posts
---

Improving [the previous implementation](/connected-circles/) to include the calculation of the distance between both circles inside the arrow shape. 

{% image "./image.png", "CSS-only connected circles with distance" %}

Still the same code structure

```html
<div class="circle" name="--a" size="150px"></div>
<div class="circle" name="--b" size="100px"></div>

<div class="arrow" x="--a" y="--b" size_x="150px" size_y="100px">
  ...
</div>
```

Drag the circles in the demo below and see how the value updates:

⚠️ Chrome-only for now ⚠️

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="wBWWKxP" data-pen-title="Connected Circles with Anchor Positioning II" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBWWKxP">
  Connected Circles with Anchor Positioning II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

And another demo with more than two circles

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="LEZZGxx" data-pen-title="Connected Circles with Anchor Positioning II" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/LEZZGxx">
  Connected Circles with Anchor Positioning II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

