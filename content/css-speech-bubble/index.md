---
layout: layouts/post.njk
title: A CSS-only Speech Bubble
description: Use CSS mask to create a speach bubble easy to adjust
date: 2022-08-18
tags: posts
---

Create a Speech Bubble using a few lines of code
* One element
* No pseudo-element
* Only 3 CSS properties
* Optimized with CSS variables


{% image "./speech-bubble.png", "A speech bubble made with CSS" %}

```css
.bubble {
  --r: 25px; /* the radius */
  --t: 30px; /* the size of the tail */
  
  padding: calc(2*var(--r)/3);
  mask: 
    radial-gradient(var(--t) at var(--_d) 0,#0000 98%,#000 102%) 
      var(--_d) 100%/calc(100% - var(--r)) var(--t) no-repeat,
    conic-gradient(at var(--r) var(--r),#000 75%,#0000 0) 
      calc(var(--r)/-2) calc(var(--r)/-2) padding-box, 
    radial-gradient(50% 50%,#000 98%,#0000 101%) 
      0 0/var(--r) var(--r) space padding-box;
}
.left {
  --_d: 0%;
  border-left: var(--t) solid #0000;
}
.right {
  --_d: 100%;
  border-right: var(--t) solid #0000;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="eYMbrJN" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/eYMbrJN">
  CSS only Speech Bubble</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [verpex.com/blog/website-tips/how-to-create-a-tooltip-speech-bubble-using-css](https://verpex.com/blog/website-tips/how-to-create-a-tooltip-speech-bubble-using-css)