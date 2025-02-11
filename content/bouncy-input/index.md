---
layout: layouts/post.njk
title: Bouncy radio buttons using modern CSS
description: A fun CSS-only experimentation to create a jumping dot between radio inputs
date: 2025-02-11
tags: posts
---

A fun CSS-only experimentation using modern features to create bouncy radio buttons. Powered by anchor positioning, `@property`, `:has()` selector, and more!


```css
@property --_x {
  syntax: "<number>";
  inherits: false;
  initial-value: 0; 
}
.container {
  --s: 1em;     /* control the size */
  --c: #009688; /* the active color */
  
  display: grid;
  position: relative;
}
.container:before {
  content: "";
  position: absolute;
  position-anchor: --checkbox;
  height: calc(var(--s)/2);
  aspect-ratio: 1;
  --_y: clamp(-1,var(--_x)*9999,1);  /* until better support for sign() */
  left: max(-80px,var(--s)/4 - var(--_x)*var(--_y)*1px);
  top: calc(anchor(top) + var(--s)/4);
  background: var(--c);
  border-radius: 50%;
  transition: top .4s linear,--_x cubic-bezier(.1,3000,.7,3000) .4s;
}
input {
  height: var(--s);
  aspect-ratio: 1;
  border: calc(var(--s)/8) solid #939393;
  border-radius: 50%;
  outline-offset: calc(var(--s)/10);
  appearance: none;
  transition: .3s .1s;
}
input:checked {
  border-color: var(--c);
  anchor-name: --checkbox;
}
/* The hacky part ... */
.container:has(label:nth-child(1) input:checked):before {--_x:.01}
.container:has(label:nth-child(2) input:checked):before {--_x:.02}
.container:has(label:nth-child(3) input:checked):before {--_x:.03}
/* .container:has(label:nth-child(N) input:checked):before {--_x:.0N}*/
```

Click for a cool effect!

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="JojjRRB" data-pen-title="Bouncy input radio!" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JojjRRB">
  Bouncy input radio!</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

And the horizontal version as well

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="MYWWjvE" data-pen-title="Bouncy input radio II" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MYWWjvE">
  Bouncy input radio II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

A related article to understand the logic behind the hacky part and the strange `cubic-bezier()`: [Advanced CSS Animation Using cubic-bezier()](https://css-tricks.com/advanced-css-animation-using-cubic-bezier/)