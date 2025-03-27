---
layout: layouts/post.njk
title: "Custom progress element using attr()"
description: Create a custom progress element with a dynamic coloration based on the value
date: 2025-03-25
tags: posts
---

Using the new `attr()` function, we can customize a progress element based on the progression. We can, for example, have a different coloration for each range of values! A single-element implementation without JavaSript.

{% image "./image.png", "CSS-only Cut-out shapes using clip-path" %}

```css
progress[value] {
  --val: attr(value type(<number>));
  --max: attr(max type(<number>),1);
  
  --_p: calc(100%*var(--val)/var(--max)); /* the percentage of progression */
  --_b: 
    /* if (p < 30%) "red" */
    conic-gradient(red    0 0) 0/calc(30% - var(--_p)) 1%,
    /* else if (p < 60%) "orange" */
    conic-gradient(orange 0 0) 0/calc(60% - var(--_p)) 1%,
    /* else "green" */
    green;
}
progress[value]::-webkit-progress-value {
  background: var(--_b);
}
progress[value]::-moz-progress-bar {
  background: var(--_b);
}
```

The support is still limited (Chrome-only for now)

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="OPJwbVJ" data-pen-title="Progress bar with dynamic coloration" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OPJwbVJ">
  Progress bar with dynamic coloration</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Here is another implementation where you can control the number of ranges and set the color for each one like an array.

```css
progress[value] {
  --n: 4; /* number of ranges */
  --c: #F04155,#F27435,#7AB317,#0D6759; /* color for each range */
  /* N=4 so we have the following ranges [0% 25%[ [25% 50%[ [50% 75%[ [75% 100%] */

  --_v: attr(value type(<number>));
  --_m: attr(max type(<number>),1);
  --_i: round(down,min(99,100*var(--_v)/var(--_m)),100/var(--n));
  --_b: linear-gradient(var(--c)) no-repeat
     0 calc(var(--_i)*var(--n)*1%/(var(--n) - 1))/100% calc(1px*infinity);
}
progress[value]::-webkit-progress-value {
  background: var(--_b);
}
progress[value]::-moz-progress-bar {
  background: var(--_b);
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="LEYJGoQ" data-pen-title="Progress bar with dynamic coloration" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LEYJGoQ">
  Progress bar with dynamic coloration</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

For better support check the following method: [Progress bar with dynamic coloration](/progress-bar-dynamic-color/)