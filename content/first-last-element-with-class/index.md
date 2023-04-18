---
layout: layouts/post.njk
title: "Select the first & last element with a class"
description: "Two methods to select the first & last element with a specific class"
date: 2023-04-18
tags: posts
---

Do you want to select the first and last element with a specific class? It's possible and you can do it using 2 different methods!


```css
/* First element with class "cat" */
.cat:not(.cat ~ *) {}
/* OR */
:nth-child(1 of .cat) {}


/* Last element with class "bird" */
.bird:not(:has(~ .bird)) {}
/* OR */
:nth-last-child(1 of .bird) {}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ExdgYXo" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExdgYXo">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

