---
layout: layouts/post.njk
title: The Sticky Header that Sticks!
description: Another fancy effect powered by scroll-driven animation and shape()
date: 2026-04-22
tags: posts
---

Creating a sticky header is an easy task with `position: sticky`. But what about a sticky header that sticks for real? By combining scroll-driven animation and `shape()`, we can achieve a nice effect with simple code.

{% image "./image.png", "A CSS-only sticky header" %}

```css
header {
  position: sticky;
  top: 0;
  animation: stick linear both;
  animation-timeline: scroll();
  animation-range: 0px 45px;
}
@keyframes stick {
  0% {
    padding-block: 30px 30px; /* 30 + 30 = 60 */
    clip-path: shape(/* code from generator */);
  }
  to {
    padding-block: 5px 55px; /* 5 + 55 = 60 */
    clip-path: shape(/* code from generator */);
  }
}
```

<p class="codepen" data-height="500" data-pen-title="A Sticky Header that Stick!" data-preview="true" data-default-tab="result" data-slug-hash="wBzbjry" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/wBzbjry">
  A Sticky Header that Stick!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The shapes are generated using my [wavy divider generator](https://css-generators.com/wavy-divider/). Choose the bottom side, then fix the shape ID and the granularity. The first shape is the one with a size equal to `0` (rectangle), and the second shape will have a size different from `0`. Having the same granularity (the same number of points) will allow the browser to transition smoothly between the two shapes.

{% image "./image1.png", "Overview of the wavy divider generator" %}