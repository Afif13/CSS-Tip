---
layout: layouts/post.njk
title: Tooltip using mask
description: Use CSS mask to create a tooltip with a gradient coloration
date: 2022-04-04
tags: posts
---

Create a Tooltip shape with rounded corners using a few lines of code
* No extra element
* No pseudo element
* Works with any background 
* Easy to control using CSS variables

{% image "./tooltip.png", "A tooltip with gradient coloration" %}

```css
.tooltip {
  --r: 30px; /* control the radius */
  --h: 50px; /* control the height of the tail */
  --p: 30%;  /* control the position of the tail */

  padding: var(--r);
  border-bottom: var(--h) solid #0000;
  mask:
    /* adjust the angles of the 1st conic-gradient to control the shape */
    conic-gradient(from 30deg at var(--p) 100%,#0000,#000 1deg 30deg,#0000 31deg)
     0 100%/100% calc(100% - var(--r)) no-repeat,
    conic-gradient(at calc(var(--r)/2) calc(var(--r)/2),#000 270deg,#0000 0)
     0 0/calc(100% - var(--r)/2) calc(100% - var(--r)/2) padding-box,
    radial-gradient(50% 50%,#000 98%,#0000) 
     0 0/var(--r) var(--r) space padding-box;
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="KKZyQBb" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KKZyQBb">
  Rounded tooltip CSS only</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Another idea with a different syntax:

```css
.tooltip {
  --r: 30px; /* control the radius */
  --h: 50px; /* control the height of the tail */
  --p: 30%;  /* control the position of the tail */

  padding: var(--r);
  border: var(--h) solid #0000;
  border-radius: calc(var(--r) + var(--h));
  mask:
    /* adjust the angles of the 1st conic-gradient to control the shape */
    conic-gradient(from 30deg at var(--p) 100%,
        #0000, red 1deg 30deg, #0000 31deg)
      0 100%/ 100% var(--h) no-repeat border-box, 
    conic-gradient(red 0 0) padding-box;
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="VwyQmLJ" data-preview="true" data-user="thebabydino" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/thebabydino/pen/VwyQmLJ">
  Rounded tooltip CSS only</a> by Ana Tudor (<a href="https://codepen.io/thebabydino">@thebabydino</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>