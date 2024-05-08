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
  --r: 1rem;   /* the radius */
  --t: 1.5em;  /* the size of the tail */
  
  border-inline: var(--t) solid #0000;
  border-radius: calc(var(--r) + var(--t))/var(--r);
  mask: 
    radial-gradient(100% 100% at var(--_p) 0,#0000 99%,#000) 
      var(--_p) 100%/var(--t) var(--t) no-repeat,
    linear-gradient(#000 0 0) padding-box;
}
.left {
  --_d: 0;
  border-bottom-left-radius: 0 0;
}
.right {
  --_d: 100%;
  border-bottom-right-radius: 0 0;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="eYMbrJN" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/eYMbrJN">
  CSS only Speech Bubble</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Speech Bubble shapes: [css-generators.com/tooltip-speech-bubble](https://css-generators.com/tooltip-speech-bubble/)