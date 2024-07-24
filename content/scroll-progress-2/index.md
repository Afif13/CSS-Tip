---
layout: layouts/post.njk
title: Calculate the scroll progress of an arbitrary element
description: A few lines of CSS to get the scroll progress of any element in the page
date: 2024-07-24
tags: posts
---

The same code of [the previous trick](/scroll-progress/) can also be used to get the scroll progress of any element on the page. The only difference is the use of `self` inside the `scroll()` value.

```css
@property --s {
  syntax: '<integer>';
  inherits: true;
  initial-value: 0; 
}
.scroll {
  animation: scroll 1s linear;
  animation-timeline: scroll(self);
}
@keyframes scroll {
  to {--s: 100}
}

.scroll:before {
  content: "Scroll Progress: " counter(s) "%";
  counter-reset: s var(--s);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="qBzaOdP" data-pen-title="CSS only scroll progress II" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBzaOdP">
  CSS only scroll progress II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>