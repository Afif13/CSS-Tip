---
layout: layouts/post.njk
title: Wavy text animation
description: Use CSS gradients to create a wavy text animation
date: 2022-04-19
tags: posts
---

Create a Wavy text animation using a few lines of code
* One element
* No pseudo element
* No duplicated text
* No SVG
* Optimized with CSS variables

{% image "./wave.png", "A text with a wavy background coloration" %}

```css
h1 {
  --c: #269af2; /* the color */
  
  --_p: 93% 83.5% at;
  --_g1: radial-gradient(var(--_p) bottom,var(--c) 79.5%,#0000 80%) no-repeat;
  --_g2: radial-gradient(var(--_p) top   ,#0000 79.5%,var(--c) 80%) no-repeat;
  background: var(--_g1),var(--_g2),var(--_g1),var(--_g2);
  -webkit-background-clip: text;
          background-clip: text;
  color: #0000;
  -webkit-text-stroke: 0.2rem var(--c);
  animation: 
    s 2s infinite alternate,
    m 3s infinite linear;
}
@keyframes m {
  0%  {background-position:-200% 100%,-100% 100%,  0% 100%,100% 100%}
  100%{background-position:   0% 100%, 100% 100%,200% 100%,300% 100%}
}
@keyframes s{
  0%  {background-size: 50.5% 80%}
  33% {background-size: 50.5% 70%}
  66% {background-size: 50.5% 85%}
  100%{background-size: 50.5% 95%}
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="MWrZPoB" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MWrZPoB">
  CSS only Wavy text</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
