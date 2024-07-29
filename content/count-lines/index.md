---
layout: layouts/post.njk
title: Count the number of lines inside a text
description: A CSS-only solution to count the lines of text
date: 2024-07-29
tags: posts
---

By adjusting the code of [the previous tip (getting the width/height of any element)](/element-dimension/) we can do some intresting counting. For example, we can count the number of lines inside a text.

```css
@property --_y {
  syntax: "<number>";
  inherits: true;
  initial-value: 0; 
}
@property --h {
  syntax: "<integer>";
  inherits: true;
  initial-value: 0; 
}
body {
  timeline-scope: --cy;
}
/* the text container  */
.container {
  overflow: auto;
  position: relative;
}
.container:before {
  content:"";
  position: absolute;
  left: 0;
  top: 0;
  height: 1lh; /* instead of 1px we use 1lh (the height of a line box) */
  view-timeline: --cy block;
}
/* the element that will show the count */
.count {
  --h:calc(1/(1 - var(--_y)));
  animation: y 1s linear;
  animation-timeline: --cy;
  animation-range: entry 100% exit 100%;
}
.count:before {
  content: counter(h);
  counter-reset: h var(--h);
}
@keyframes y {to{--_y:1}}
```

Here is a static demo:

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="BagKWdm" data-pen-title="Counting the number of lines inside a text" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/BagKWdm">
  Counting the number of lines inside a text</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Here is a version where you can edit the content. The number of lines will adjust based on the content you will enter.

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="RwzapLK" data-pen-title="Dynamic line counting" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RwzapLK">
  Dynamic line counting</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [frontendmasters.com/blog/how-to-get-the-width-height-of-any-element-in-only-css](https://frontendmasters.com/blog/how-to-get-the-width-height-of-any-element-in-only-css/)