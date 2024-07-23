---
layout: layouts/post.njk
title: Calculate the scroll progress of the page
description: A few lines of CSS to get the scroll progress of the page inside a CSS variable
date: 2024-07-23
tags: posts
---

Get the scroll progress of the page as a CSS variable using a few lines of code
* Powered by Scroll-Driven animations
* Defined at the `:root` level (avaiable to all the elements) 
* Typed using @property
* You can easily use it within any formula


```css
@property --s {
  syntax: '<integer>';
  inherits: true;
  initial-value: 0; 
}
:root {
  animation: scroll 1s linear;
  animation-timeline: scroll();
}
@keyframes scroll {
  to {--s: 100}
}

element:before {
  content: counter(s) "%";
  counter-reset: s var(--s);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="dyBXjYe" data-pen-title="CSS only scroll progress " data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dyBXjYe">
  CSS only scroll progress </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>