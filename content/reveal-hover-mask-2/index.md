---
layout: layouts/post.njk
title: A reveal hover effect using CSS mask II
description: Use CSS mask to create a nice reveal effect on hover
date: 2023-07-21
tags: posts
---

Another variation of [the previous hover effect](/reveal-hover-mask) with a diagonal reveal. Using the same code structure.
* No extra element (only the `<img>` tag)
* Less than 10 CSS declarations
* Powered by CSS mask and CSS gradients


{% image "./image.png", "A diagonal reveal effect using mask" %}

```css
img {
  padding: 10px; /* control the space for the gradient */
  background: repeating-linear-gradient(45deg,#FF6B6B 0 10px,#4ECDC4 0 20px);
  --g: content-box 50% 50%/200% 200% no-repeat;
  mask:
    linear-gradient(#000 0 0),
    linear-gradient(calc(135deg + var(--a,0deg)),#000 50.1%,#0000 0) var(--g),
    linear-gradient(calc(-45deg + var(--a,0deg)),#000 50.1%,#0000 0) var(--g);
  mask-composite: exclude, add;
  transition: .5s;
}
img:hover {
  mask-position: 0% 0%,100% 100%;
}
/* we update the angle for the alternative version */
img.alt {
  --a: 90deg
}
/* and the X movement */
img.alt:hover {
  mask-position: 100% 0%,0% 100%;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="qBQKMKa" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBQKMKa">
  Hover reveal animation using mask II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

And why not the Zig-Zag version as well


{% image "./image-2.png", "A Zig-Zag reveal hover effect using mask" %}


<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="vYQaLaZ" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/vYQaLaZ">
  Hover reveal animation using mask III</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More Detail: [www.smashingmagazine.com/2023/09/revealing-images-css-mask-animations](https://www.smashingmagazine.com/2023/09/revealing-images-css-mask-animations/)