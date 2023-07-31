---
layout: layouts/post.njk
title: A reveal animation with a rotating square
description: a fancy animation on hover using clip-path
date: 2023-07-31
tags: posts
---

Add a fancy reveal animation to your image on hover
* No extra element (only the `<img>` tag)
* Powered by Trigonometric functions and @property
* Optimized with CSS variables


{% image "./image.png", "A reveal animation with a rotating square" %}

```css
@property --a { 
  syntax: "<angle>";
  initial-value: 0deg; 
  inherits: true;
}
@property --d { 
  syntax: "<percentage>";
  initial-value: 0%; 
  inherits: true;
}
img {
  --b: 10px; /* control the border thickness */
  --g: 20px; /* control the gap */
  
  --d: 30%;
  --a: 45deg;
  --_o:50% + (var(--d) + var(--g) + var(--b));
  --_i:50% + (var(--d) + var(--g));
  --_f:50% + (var(--d));
  clip-path: polygon(
    /*  */
    calc(var(--_o)*sin(-45deg + var(--a))) calc(var(--_o)*cos(-45deg + var(--a))),
    calc(var(--_o)*sin( 45deg + var(--a))) calc(var(--_o)*cos( 45deg + var(--a))),
    calc(var(--_o)*sin(135deg + var(--a))) calc(var(--_o)*cos(135deg + var(--a))),
    calc(var(--_o)*sin(225deg + var(--a))) calc(var(--_o)*cos(225deg + var(--a))),
    calc(var(--_o)*sin(-45deg + var(--a))) calc(var(--_o)*cos(-45deg + var(--a))),
    /*  */
    calc(var(--_i)*sin(-45deg + var(--a))) calc(var(--_i)*cos(-45deg + var(--a))),
    calc(var(--_i)*sin(225deg + var(--a))) calc(var(--_i)*cos(225deg + var(--a))),
    calc(var(--_i)*sin(135deg + var(--a))) calc(var(--_i)*cos(135deg + var(--a))),
    calc(var(--_i)*sin( 45deg + var(--a))) calc(var(--_i)*cos( 45deg + var(--a))),
    calc(var(--_i)*sin(-45deg + var(--a))) calc(var(--_i)*cos(-45deg + var(--a))),
    /*  */
    calc(var(--_f)*sin(-45deg + var(--a))) calc(var(--_f)*cos(-45deg + var(--a))),
    calc(var(--_f)*sin( 45deg + var(--a))) calc(var(--_f)*cos( 45deg + var(--a))),
    calc(var(--_f)*sin(135deg + var(--a))) calc(var(--_f)*cos(135deg + var(--a))),
    calc(var(--_f)*sin(225deg + var(--a))) calc(var(--_f)*cos(225deg + var(--a))),
    calc(var(--_f)*sin(-45deg + var(--a))) calc(var(--_f)*cos(-45deg + var(--a)))
  );
  outline: 166px solid #2c2c2c; /* color here */
  transition: --d .3s,--a .2s .2s;
}
img:hover {
  --a: 0deg;
  --d: 71%;
  transition: --a .3s,--d .2s .2s;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="YzRdWXQ" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/YzRdWXQ">
  Rhombus rotation on hover</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


