---
layout: layouts/post.njk
title: Get the scrollbar width using only CSS
description: A few lines of code to get the scrollbar width within a CSS variable
date: 2024-11-14
tags: posts
---

Do you want to know the scrollbar width? It's possible using only CSS and a few lines of code! You can get the pixel value within a CSS variable and use it everywhere.

As a bonus, you can also have an integer value!

```css
@property --scrollbar {
  syntax: "<length>";
  inherits: true;
  initial-value: 0px; 
}
html {
  container-type: size;
}
body {
  --scrollbar: calc(100vw - 100cqw);
  /* 
     100cqw is the html width  
     100vw  is the viewport width 
     the difference is the scrollbar width 🤩
  */
}

/* As a bonus, you can have an interger value and show it */
body:before {
  content: counter(val) "px";
  counter-reset: val tan(atan2(var(--scrollbar),1px));
}
```

Tested on Chrome

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="MWNLNvz" data-pen-title="CSS-only scrollbar width" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWNLNvz">
  CSS-only scrollbar width</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>