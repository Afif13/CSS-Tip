---
layout: layouts/post.njk
title: A CSS-only array of colors
description: Create an array of colors and use an index to navigate 
date: 2023-06-26
tags: posts
---

Do you want to define an array of colors using only CSS? Yes, it's possible! It's limited to only background coloration but can be useful in many situations.

Use an index like any programming language to iterate through the array. Practical when you are already using an index for something else.


{% image "./image.png", "Boxes with different colors" %}

```css
.box {
  --colors: red, blue, green, purple; /* colors array */
  --n: 4; /* length of the array  */
  --i: 0; /* index of the color [0 to N-1] */
  
  background:
    linear-gradient(var(--colors)) no-repeat
     0 calc(var(--i)*100%/(var(--n) - 1))
     /100% calc(1px*infinity); /* yes infinity is doing the magic */
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="KKrNYyp" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKrNYyp">
  Colors array using only CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

If you want to work with only 2 colors, I have a better version: [Color Switch Using Color-Mix()](https://css-tip.com/color-switch-color-mix/)