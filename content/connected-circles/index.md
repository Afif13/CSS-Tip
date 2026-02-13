---
layout: layouts/post.njk
title: Connecting Circles With Anchor Positioning
description: Using modern CSS to create a dynamic link that connects two circles, whatever their position
date: 2025-12-16
tags: posts
---

Let's suppose you have two circles randomly placed on the page, and you want to create a connection between them. Sounds like a JavaScript job, but CSS can also do it. 

A good overview of what can be possible using modern features such as Anchor Positioning, `attr()`, container queries, `shape()`, trigonometric functions, and more!

{% image "./image.png", "CSS-only connected circles" %}

With a simple HTML/CSS configuration, you have an arrow fully controlled using CSS. Not only is the position dynamic, but the shape adjusts according to the distance between the circles. And if they touch each other, the link disappears. Collision detection using pure CSS!

```html
<div class="circle" name="--a" size="150px"></div>
<div class="circle" name="--b" size="100px"></div>

<div class="arrow" x="--a" y="--b" size_x="150px" size_y="100px">
  ...
</div>
```

Drag the circles in the demo below and see how the arrow behaves:

⚠️ Chrome-only for now ⚠️

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="PwNrNvP" data-pen-title="Connected Circles with Anchor Positioning" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/PwNrNvP">
  Connected Circles with Anchor Positioning</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

You can easily have as many circles as you want!

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="dPMBMBE" data-pen-title="Connected Circles with Anchor Positioning" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPMBMBE">
  Connected Circles with Anchor Positioning</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

