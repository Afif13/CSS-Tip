---
layout: layouts/post.njk
title: A Sparkle shape with one gradient
description: Create a fancy sparkle shape using only one gradient
date: 2024-05-09
tags: posts
---

How much code is needed to create a Sparkle shape? ✨

Only one gradient and you can easily get the border-only variation.


{% image "./image.png", "CSS-only sparkle shape" %}

```css
.sparkle {
  background: 
    radial-gradient(#0000 71%,#F8CA00 72% var(--_b,)) 
    10000% 10000%/99.5% 99.5%;
}
.border {
  --b: 10px; /* control the thickness */
  --_b: calc(71% + var(--b)),#0000 calc(72% + var(--b));
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="eYaYzxX" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/eYaYzxX">
  Sparkle shape with one gradient</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

And if you consider `mask` you can have a gradient coloration

```css
.sparkle {
  background: linear-gradient(45deg,#F8CA00,#fe7496);
  mask: 
    radial-gradient(#0000 71%,#F8CA00 72% var(--_b,)) 
    10000% 10000%/99.5% 99.5%;
}
.border {
  --b: 10px; /* control the thickness */
  --_b: calc(71% + var(--b)),#0000 calc(72% + var(--b));
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="YzbzGZQ" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/YzbzGZQ">
  Sparkle shape with gradient coloration</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More CSS Shapes: [css-shape.com](https://css-shape.com)