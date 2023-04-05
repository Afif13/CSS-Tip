---
layout: layouts/post.njk
title: Fade content inside border using mask
description: Use CSS mask to fade your content inside border
date: 2023-03-30
tags: posts
---

Create a fading content while keeping the border visible using CSS mask. It works with `border-radius` and no need to know the value of border.


```css
.box {
  border: 4px solid orange; /* we don't need to know the border-width */
  mask:
    linear-gradient(#000 0 0), 
    /* fade only the padding area 
       (in the opposite direction) */
    linear-gradient(#0000,#000 90%) padding-box;
  mask-composite: exclude;
}
```

{% image "./fade-content-inside-border.png", "A fading content" %}

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="qBMGZQz" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBMGZQz">
  Fading content inside border II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

A different idea without `mask-composite` but it won't work with `border-radius` and you need to know the `border-width`.

```css
.box {
  --b: 4px; /* border thickness */
  
  border: var(--b) solid orange;
  mask:
    /* keep the border visible */
    conic-gradient(from 90deg at calc(2*var(--b)) calc(2*var(--b)),#0000 25%,#000 0)
    calc(-1*var(--b)) calc(-1*var(--b)), 
    /* fade the content */
    linear-gradient(#000,#0000 90%);
}
```

Online demo: [https://codepen.io/t_afif/pen/YzObqzg](https://codepen.io/t_afif/pen/YzObqzg)

