---
layout: layouts/post.njk
title: Fluid typography with discrete steps 
description: Improve your fluid typography implementation using the round() function
date: 2024-04-03
tags: posts
---

Use the `round()` function and create a fluid typography with a discrete function instead of a continuous one.

Define the step and get precise values within a specific range. Very useful if you have some calculation based on the `font-size` like using the `em` unit. No more rounding issue!


```css
/* Instead of  */
p {
  font-size: clamp(1rem,1rem + 3vw,2.5rem);
}
/* use */
p {
  font-size: clamp(1rem,round(down,1rem + 3vw,2px),2.5rem);
  
  /* 
   1rem = 16px | 2.5rem = 40px
   we go from 16px to 40px with a 2px step
   16px,18px,20px,22px,24px,..,38px,40px
  */
  
  /* OR a more friendly syntax*/
  --fluid: clamp(1rem,1rem + 3vw,2.5rem); /* the original function */
  font-size: round(down,var(--fluid),2px);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="RwOxLNQ" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RwOxLNQ">
  Fluid typography with steps</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>