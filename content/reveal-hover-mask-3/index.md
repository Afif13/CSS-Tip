---
layout: layouts/post.njk
title: A reveal hover effect using CSS mask III
description: Use CSS mask to create a nice reveal effect on hover
date: 2023-08-09
tags: posts
---

Add a nice reveal animation to your image with a few lines of code
* No extra element (only the `<img>` tag)
* No pseudo-elements
* Powered by CSS Mask & @property


{% image "./image.png", "A reveal hover effect using mask & @property" %}

```css
@property --p {
  syntax: "<percentage>";
  initial-value: 0%;
  inherits: false;
}

img {
  --b: 10px; /* border thickness */
  --g: 8px;  /* the gap */ 
  
  border: var(--b) solid #0000;
  padding: var(--g);
  border-radius: 50%;
  background: 
    repeating-conic-gradient(#F7E4BE 0 9deg,#7A6A53 10deg 18deg) /* the border coloration */
    border-box;
  --m:linear-gradient(#000 0 0);
  mask: 
    var(--m),var(--m) padding-box,
    conic-gradient(#000 var(--p,0%),#0000 0) content-box;
  mask-composite: exclude;
  transition: --p .5s;
}
img:hover {
  --p: 100%;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="ZEmNeag" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEmNeag">
  Hover Reveal Animation </a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>