---
layout: layouts/post.njk
title: Select all elemens between two class names
description: A simple selector to select all the elements between two given classes
date: 2023-05-02
tags: posts
---

Do you want to select all the elements between two different class names? Use the :not() selector to do it


```css
.start ~ :not(.end,.end ~ *) {
  
}
```


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="QWZqpYN" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QWZqpYN">
  Select elements between two classes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
