---
layout: layouts/post.njk
title: Put a number inside boxes
description: A few trick to make your number look fancy
date: 2022-08-02
tags: posts
---

Make your numbers look fancy by placing each digit inside its own box.
* Only one element
* Easy to control using CSS variables
* Two versions: Full & Border-only
* No restriction on the number length


{% image "./number-box.png", "A number where each digit is inside a box" %}

```css
.number {
  --c: #C02942; /* control the colors */
  --w: 0.5ch;   /* control the width for each number */
  --g: 10px;    /* control the gap between numbers */

  letter-spacing: var(--w);
  font-family: monospace;
  color: #fff;
  background: var(--c);
  mask: 
    repeating-linear-gradient(90deg,
        #000  0 calc(1ch + var(--w) - var(--g)), 
        #0000 0 calc(1ch + var(--w)))
    0/calc(100% - var(--w)/2) 100% no-repeat;
  padding-left: calc((var(--w) - var(--g))/2);
  margin-right: calc(var(--w)/-2);
}
.number.border {
  --b: 4px; /* control the border */
  
  color: #000;
  --_g: var(--b), #0000 90deg,var(--c) 0;
  background:
    conic-gradient(from  90deg at var(--b) var(--_g)),
    conic-gradient(from -90deg at right calc(var(--b) + var(--g)) bottom var(--_g));
   background-size: calc(1ch + var(--w)) 100%;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="MWVQmBv" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWVQmBv">
  Numbers in boxes (CSS only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>