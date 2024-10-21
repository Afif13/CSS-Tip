---
layout: layouts/post.njk
title: How to correctly define a one-color gradient
description: The most optimized way to create a one-color gradient
date: 2024-10-21
tags: posts
---

Learn the correct way to create a one-color gradient with an optimized code. Stop using default values and save some space!

All the below are the same. You can save up to 32 chars!

```css
.gradient {
  background: linear-gradient(75deg,#D95B43 0%,#D95B43 100%);/* 46 chars */
  /* you don't need the angle if it's the same color */
  background: linear-gradient(#D95B43 0%,#D95B43 100%);      /* 40 chars */
  /* you can remove the 0% and 100%, they are implicit */
  background: linear-gradient(#D95B43,#D95B43);              /* 32 chars */
  /* if it's the same color, write it once with two color stops 
     the color stops don't matter so use the shortest one
  */
  background: linear-gradient(#D95B43 0 0);                  /* 28 chars */
  /* if it's a one-color gradient any type of gradient will do the job
     so pick the conic-gradient() as it's one character shorter
  */
  background: conic-gradient(#D95B43 0 0);                   /* 27 chars */
  
  
  /* In the near future, we can also remove the color stops */
  background: conic-gradient(#D95B43);                       /* 23 chars */
  /* In another future, we will have a better function to create 
     a one-color image (yes, gradients are images)
  */
  background: image(#D95B43);                                /* 14 chars */
}
```

Where you need a one-color gradient? Everywhere!

Hover Effects: [css-tricks.com/cool-hover-effects-using-background-properties](https://css-tricks.com/cool-hover-effects-using-background-properties/)

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="xxXNpBW" data-pen-title="hover effect" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xxXNpBW">
  hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

CSS Loaders: [css-tricks.com/single-element-loaders-the-bars](https://css-tricks.com/single-element-loaders-the-bars/)

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="mdWVOrR" data-pen-title="The bars" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdWVOrR">
  The bars</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Decorations and shapes with `border-image`: [smashingmagazine.com/2024/01/css-border-image-property](https://www.smashingmagazine.com/2024/01/css-border-image-property/)

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="XWoNdGK" data-pen-title="Infinite image shadow" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWoNdGK">
  Infinite image shadow</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="ExrEXoO" data-pen-title="A simple Tooltip using 2 CSS properties" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ExrEXoO">
  A simple Tooltip using 2 CSS properties</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Masking: [css-tip.com/border-gradient](https://css-tip.com/border-gradient/)

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="ZEdYKvo" data-pen-title="Gradient borders with rounded corners" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEdYKvo">
  Gradient borders with rounded corners</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

And many more!