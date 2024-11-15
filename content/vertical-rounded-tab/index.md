---
layout: layouts/post.njk
title: Vertical rounded tabs using CSS mask
description: A few lines of code to get vertical rounded tabs using CSS mask
date: 2024-11-15
tags: posts
---

Updating the previous [rounded tab shape](/rounded-tab/) to create the [vertical version](https://css-shape.com/vertical-rounded-tab/) using the same code structure.
* No extra element & No pseudo-element
* One variable to control the curvature
* Works with gradient coloration
* Powered by CSS mask


{% image "./image.png", "CSS-only vertical rounded tabs using CSS mask" %}

```css
.rounded-tab {
  --r: .8em; /* control the radius/curvature */

  border-block: var(--r) solid #0000;
  border-radius: var(--r) 0 0 var(--r)/calc(2*var(--r));
  mask: 
    radial-gradient(var(--r) at 0 var(--r),#0000 98%,#000 101%)
      100% calc(-1*var(--r))/var(--r) 100% repeat-y,
    conic-gradient(#000 0 0) padding-box;
}
.rounded-tab.alt {
  border-radius: 0 var(--r) var(--r) 0/calc(2*var(--r));
  mask: 
    radial-gradient(var(--r) at 100% var(--r),#0000 98%,#000 101%)
      0 calc(-1*var(--r))/var(--r) 100% repeat-y,
    conic-gradient(#000 0 0) padding-box;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="ExqrYyW" data-pen-title="Vertical rounded tabs using CSS mask" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExqrYyW">
  Vertical rounded tabs using CSS mask</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com)