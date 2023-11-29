---
layout: layouts/post.njk
title: A Ribbon shape with a reveal hover effect
description: A CSS-only ribbon shape with a fancy reveal effect on hover
date: 2023-11-29
tags: posts
---

Create a ribbon shape with a fancy reveal effect on hover
* Only one element
* No fixed size (it fits your text content)
* Optimized with CSS Variables


{% image "./image.png", "CSS Ribbon shape with reveal effect" %}

```css
@property --s { 
  syntax: "<length-percentage>";
  initial-value: 0%;
  inherits: true;
}

.ribbon {
  --r: .8em; /* control the cutout */
  --s: 15%; /* control how much content is shown initially */
  
  margin-block: .5em;
  padding-inline: calc(var(--r) + .3em) .5em;
  clip-path: polygon(0 0,var(--s) 0,var(--s) 100%,0 100%,0 calc(100% - .25em),var(--r) 50%,0 .25em) margin-box;
  translate: calc(100% - var(--s));
  background: #2699dc padding-box;
  position: relative;
  transition: --s .8s linear;
}
.ribbon:before {
  content: "";
  position: absolute;
  inset: -.5em calc(100% - var(--s)) -.5em 0;
  background: radial-gradient(.2em 50% at right,#000a,#0000);
}
.ribbon:hover {
  --s: 100%;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="poGZGZY" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/poGZGZY">
  Ribbon shapes with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We can easily get more variation using the same code structure

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="BaMOozG" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/BaMOozG">
  Ribbon shapes with hover effect (more variation)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>