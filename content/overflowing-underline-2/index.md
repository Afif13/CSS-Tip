---
layout: layouts/post.njk
title: Extend your underline to the edge of the screen II
description: Use a border-image trick to create an overflowing underline
date: 2022-06-20
tags: posts
---

Improving [the previous effect](/overflowing-underline/) to consider an underline with a gradient coloration that extend to the edge of the screen
* No extra element
* No pseudo-element
* No overflow issue
* Optimized with CSS variables

{% image "./line.png", "An extended underline to left and the right" %}

```css
.full-line {
  --b: 8px; /* border thickness */
  --g: repeating-linear-gradient(45deg,#BD1550 0 10px,#E97F02 0 20px,#F8CA00 0 30px);
  border-image: var(--g) fill 0/calc(100% - var(--b)) 0 0/0 100vw 0 0 repeat;
  padding-block: 10px;
}
.left {
  border-image-outset: 0 0 0 100vw;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="mdXYyRg" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdXYyRg">
  CSS only extended underline with gradient </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related: [smashingmagazine.com/2024/01/css-border-image-property/](https://www.smashingmagazine.com/2024/01/css-border-image-property/)