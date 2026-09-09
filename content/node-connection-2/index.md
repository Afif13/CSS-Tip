---
layout: layouts/post.njk
title: Dynamic Node Connection (CSS-only Diagram) II
description: More node connections using border-shape and modern CSS
date: 2026-09-09
tags: posts
---

Extending [the previous implementation](/node-connection/) to add more connection types. This time, the connectors will stick to the specified sides, regardless of the node's position. Another cool demo made possible with anchor positioning, `border-shape`, `shape()`, container queries, `if()`, and more!

{% image "./image.png", "CSS-only diagram" %}


Drag the nodes in the demo below and see the magic in play!

⚠️ Chromium-only for now ⚠️

<p class="codepen" data-height="700" data-pen-title="CSS-only diagram with dynamic connections II" data-preview="true" data-default-tab="result" data-slug-hash="MYpewWq" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MYpewWq">
  CSS-only diagram with dynamic connections II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

I used three types of connections.

A left-to-right connection:

<p class="codepen" data-height="600" data-pen-title="left-to-right connection" data-preview="true" data-default-tab="result" data-slug-hash="myWEJmm" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/myWEJmm">
  left-to-right connection</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

A left-to-left connection:

<p class="codepen" data-height="600" data-pen-title="Left-to-left connection" data-preview="true" data-default-tab="result" data-slug-hash="EaWyjXY" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaWyjXY">
  Left-to-left connection</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


A right-to-right connection:

<p class="codepen" data-height="600" data-pen-title="right-to-right connection" data-preview="true" data-default-tab="result" data-slug-hash="myWEJwm" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/myWEJwm">
  right-to-right connection</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The possibilities are endless. Stay tuned for more CSS-only diagrams!
