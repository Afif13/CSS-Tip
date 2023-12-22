---
layout: layouts/post.njk
title: Add a 3D style to your text III
description: Add a touch of 3D to your text with some gradients tricks
date: 2023-12-22
tags: posts
---

Add a cool 3D effect to your name or your favorite number
* Only one element per word (not per letter)
* No pseudo-elements
* Optimized with CSS variables


{% image "./image.png", "A 3D text using CSS" %}

```css
h2 {
  --s: .4em; /* space between boxes*/
  --d: .2em; /* the depth */
  --p: .3em; /* the inline padding */
  
  font-family: monospace; /* only for monospace font */
  line-height: 1.5; /* control the height of the boxes */
  letter-spacing: calc(var(--s) + var(--d) + 2*var(--p));
  padding-left: var(--p);
  padding-bottom: var(--d);
  clip-path: inset(0 calc(var(--p) + var(--s)) 0 0);
  --_g:calc(1ch + var(--s) + var(--d) + 2*var(--p));
  background:
    conic-gradient(at calc(100% - var(--d) - var(--s)) calc(100% - var(--d)),
                    #0008 37.5%,#0004 75%,#0000 0) 0 0/var(--_g) 100%
    #8A9B0F; /* the main color */
  mask:
    conic-gradient(from -45deg at calc(100% - var(--s)) var(--d),#0000 62.5%,#000 0)
     0 0/var(--_g) 50% repeat-x,
    conic-gradient(at var(--s) calc(100% - var(--d)),#000 37.5%,#0000 0)
     calc(-1*var(--s)) 100%/var(--_g) 50% repeat-x;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="MWxWWEM" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWxWWEM">
  CSS-only 3D letters</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>