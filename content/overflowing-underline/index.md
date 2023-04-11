---
layout: layouts/post.njk
title: Extend your underline to the edge of the screen
description: Use a border-image trick to create an overflowing underline
date: 2022-06-16
tags: posts
---

Add an underline to your title and extend it to the right (or left) edge of the screen whatever the element/container size
* No extra element
* No pseudo-element
* No overflow issue
* Only one CSS property

{% image "./line.png", "An extended underline to left and the right" %}

```css
.full-line-right {
  border-image: 
    linear-gradient(0deg,
      #1095c1 5px, /* color and thickness */
    #0000 0) fill 0//0 100vw 0 0;

}
.full-line-left {
  border-image: 
    linear-gradient(0deg,
      #c32e2e 5px,
    #0000 0) fill 0//0 0 0 100vw;
}
```
<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="yLvwgNy" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLvwgNy">
  CSS only extended underline</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>