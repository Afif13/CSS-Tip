---
layout: layouts/post.njk
title: Bending a Straight Line using Modern CSS
description: Using border-shape and anchor positioning to create a bending line between two circles
date: 2026-05-28
tags: posts
---

Updating [the previous implementation](/connected-circles-3/) with another idea of connection. This time, it's a straight line that adjusts based on the distance between the two circles. It bends when they get closer and stretches (becomes thinner) when they get farther. Implementing physics using pure CSS!

Another demo powered by modern CSS (Anchor Positioning, `border-shape`, `if()`, and more).

{% image "./image.png", "CSS-only connected circles with curved line" %}

Drag the circles and see the magic in play!

⚠️ Chrome-only for now ⚠️

<p class="codepen" data-height="600" data-pen-title="Bending a straight line using pure CSS" data-preview="true" data-default-tab="result" data-slug-hash="yyVPKzb" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yyVPKzb">
  Bending a straight line using pure CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

You can have as many elements as you want and adjust the connection setting (line length and number of curves)

<p class="codepen" data-height="600" data-pen-title="Bending a straight line using pure CSS II" data-preview="true" data-default-tab="result" data-slug-hash="ZYBaxaX" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZYBaxaX">
  Bending a straight line using pure CSS II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
