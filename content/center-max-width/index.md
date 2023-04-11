---
layout: layouts/post.njk
title: max-width + centering with one instruction
description: Use max() to center your element and set a max-width
date: 2021-12-10
tags: posts
---

Set `max-width` and center your block element with one CSS declaration using `margin-inline` and `max()`.

{% image "./image.png", "Centering and settin a max-width using max()" %}


```css
margin-inline: max(0px,50% - 800px/2);
```

You can also set a minimum margin for small screen by replacing `0px` with any value

```css
margin-inline: max(1rem,50% - 800px/2);
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="jOGMMMG" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jOGMMMG">
  margin-inline</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>