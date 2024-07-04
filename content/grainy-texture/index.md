---
layout: layouts/post.njk
title: Grainy texture using CSS gradients
description: A simple code to create a random-style background to simulate a grainy texture
date: 2024-07-02
tags: posts
---

Create a random-style background (grainy texture) using a few lines of code.

{% image "./image.png", "grainy background texture" %}

```css
html {
  --s: 6px; /* control the size */
  
  --g: repeating-conic-gradient(#774F38 0 25%,#ECE5CE 0 50%) 0/;
  background:
    var(--g) calc(1*var(--s)) calc(7*var(--s)),
    var(--g) calc(2*var(--s)) calc(5*var(--s)),
    var(--g) calc(3*var(--s)) calc(3*var(--s)),
    var(--g) calc(5*var(--s)) calc(2*var(--s)),
    var(--g) calc(7*var(--s)) calc(1*var(--s));
  background-blend-mode: darken;
}
```
<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="QWReqEx" data-pen-title="Random CSS background" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/QWReqEx">
  Random CSS background</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another example

{% image "./image2.png", "CSS-only random background texture" %}

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="mdYNxzo" data-pen-title="grainy-random CSS background II" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdYNxzo">
  grainy-random CSS background II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>