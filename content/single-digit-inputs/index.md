---
layout: layouts/post.njk
title: Single-digit inputs with one element (OTP)
description: Turn a simple input into an One Time Password field
date: 2024-05-14
tags: posts
---

Turn a simple input into single-digit inputs using a few lines of CSS. Useful for One-Time Password fields.
* No extra element (only the `<input>` element)
* Less than 15 CSS declarations
* Optimized with CSS variables


{% image "./image.png", "CSS-only One-Time Password field" %}

```css
input[type=text] {
  --w: 1ch;   /* control the width for each letter */
  --g: .15em; /* the gap between letters */
  --b: 2px;   /* the border thickness */
  --n: 6;     /* the number of letters */
  
  --c: #888;
  line-height: 1.5; /* control the height */
  letter-spacing: var(--w);
  font-family: monospace;
  width: calc(var(--n)*(1ch + var(--w)));
  padding-left: calc((var(--w) - var(--g))/2);
  clip-path: inset(0 calc(var(--w)/2) 0 0);
  background:
    repeating-linear-gradient(90deg,
      var(--c) 0 var(--b),#0000 0 calc(1ch + var(--w) - var(--g) - var(--b)),
      var(--c) 0 calc(1ch + var(--w) - var(--g)),#0000 0 2ch),
    conic-gradient(at calc(100% - var(--g) - 1px) var(--b),#0000 75%,var(--c) 0) 
     0 0/calc(1ch + var(--w)) calc(100% - var(--b));
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="XWwbMNO" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XWwbMNO">
  Single digit inputs with one element</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>