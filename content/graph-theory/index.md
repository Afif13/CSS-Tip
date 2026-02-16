---
layout: layouts/post.njk
title: Graph Theory using Modern CSS
description: A CSS-only implementation of a shortest path algorithm
date: 2026-02-16
tags: posts
---

Let's suppose you have a graph with a known number of nodes and you want to identify the shortest path between two nodes. It's possible using only CSS!

{% image "./image.png", "CSS only shortest path algorithm" %}

Not only can we draw the graph (using my previous implementation of [connecting two circles](/connected-circles-2/)), but we can also do various calculations to find the shortest path (using the technique of [getting the width/height of any element](/element-dimension/))

Drag the different nodes in the demo below to see the magic in play!

⚠️ Chrome-only for now ⚠️

<p class="codepen" data-height="700" data-default-tab="result" data-slug-hash="YPWMmOP" data-pen-title="Graph Theory (Chrome-only)" data-preview="true" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/YPWMmOP">
  Graph Theory (Chrome-only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Except for the drag feature, which relies on JS, everything else is controlled using CSS.