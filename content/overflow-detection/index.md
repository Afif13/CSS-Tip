---
layout: layouts/post.njk
title: Overflow/scrollbar detection using modern CSS 
description: Using scroll-driven animations you can detect when an element is overflowing or has a scrollbar
date: 2024-12-10
tags: posts
---

Do you want to detect if an element is having an overflow or if it's scrollable? It's possible with scroll-driven animation! You can also store this information within a variable at `:root` level and do whatever you want (like styling any elements on the page)

```css
:root {
  timeline-scope: --scroll;
  animation: --scroll forwards;
  animation-timeline: --scroll;
  container: --scroll/inline-size;
}
.box { /* the concerned element */
  overflow: auto; /* or hidden */
  scroll-timeline: --scroll;
}
@keyframes --scroll {
  0%,to{--scroll: 1;}
}
@container --scroll style(--scroll: 1) {
  /* The CSS when .box is overflowing 
     you can target any element on the page!
  */
}
/* Yes you can use --scroll everywhere! */
```

Resize the `.box` element in the demo below and see the magic! (chrome only for now)

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="GgKZBWX" data-pen-title="Overflow detection using only CSS" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GgKZBWX">
  Overflow detection using only CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

The use of style query is not mandatory and you can have a simpler version if you want to target the concerned element.

```css
.box {
  overflow: auto; /* or hidden */
  animation: scrolling forwards;
  animation-timeline: scroll(self);
}
@keyframes scrolling {
  0%,to{
    /* the CSS applied to .box when it has overflow */
  }
}
``` 

Or a child element

```css
.box {
  overflow: auto; /* or hidden */
}
.box .child {
  animation: scrolling forwards;
  animation-timeline: scroll(); /* it will consider the ancestor having overflow: auto/hidden  */
}
@keyframes scrolling {
  0%,to{
    /* the CSS applied to .child when .box has overflow */
  }
}
``` 

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="ZYzOaZp" data-pen-title="Overflow detection using only CSS (simple version)" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZYzOaZp">
  Overflow detection using only CSS (simple version)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>