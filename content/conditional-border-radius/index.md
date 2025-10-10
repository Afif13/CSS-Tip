---
layout: layouts/post.njk
title: Conditional Border Radius with Modern CSS
description: A simple trick to control the border-radius based on the screen/container size
date: 2025-10-10
tags: posts
---

Toggle the value of `border-radius` based on the container/screen size using a simple line of code. 

{% image "./image.png", "Conditional Border Radius with CSS" %}

```css
.box {
  border-radius: calc(sign(100cqi - 100%)*2rem);
}
```

The default value is equal to `2rem`. When the element is full width (its width equals the container width), the radius is set to `0`. `100cqi` will fallback to `100vw` (screen width) if no container is defined.

Resize the screen or the container in the demo below to see the result:

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="zxrwVPP" data-pen-title="Conditional Border Radius" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxrwVPP">
  Conditional Border Radius</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


Related: [ishadeed.com/article/conditional-border-radius](https://ishadeed.com/article/conditional-border-radius/) 