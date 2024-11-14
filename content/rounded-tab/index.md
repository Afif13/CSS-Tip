---
layout: layouts/post.njk
title: Rounded tabs with inner curves
description: A few lines of code to get rounded tabs using CSS mask
date: 2024-04-04
tags: posts
---

Use modern CSS to create those famous [rounded tabs](https://css-shape.com/rounded-tab/) with inner curves. 
* No extra element & No pseudo-element
* Less than 10 CSS declarations to get the three variations
* One variable to control the curvature
* Works with gradient coloration


{% image "./image.png", "CSS-only rounded tabs with inner curves" %}

```css
.rounded-tab {
  --r: .8em; /* control the curvature */
  
  border: solid #0000;
  border-width: 0 var(--r);
  border-radius: calc(2*var(--r)) calc(2*var(--r)) 0 0/var(--r);
  mask: 
    radial-gradient(var(--r) at var(--r) 0,#0000 98%,#000 101%)
      calc(-1*var(--r)) 100%/100% var(--r) repeat-x,
    conic-gradient(#000 0 0) padding-box;
}
.rounded-tab.left {
  border-left-width: 0;
  border-top-left-radius: var(--r);
}
.rounded-tab.right {
  border-right-width: 0;
  border-top-right-radius: var(--r);
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="JjVpPmr" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JjVpPmr">
  Rounded tab using CSS mask</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com)