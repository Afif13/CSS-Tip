---
layout: layouts/post.njk
title: 3D Box using Modern CSS
description: Combining corner-shape and modern CSS features to create a 3D box
date: 2025-09-27
tags: posts
---

In a previous post, I created a simple [3D box using `corner-shape`](/corner-shape/#cube-and-3d-box) and the border properties.

{% image "./image1.png", "CSS-only 3D box" %}

```css
.box {
  --d: 30px; /* the depth */
  
  border-radius: 0 var(--d);
  corner-shape: bevel;
  border-right:  var(--d) solid #0004;
  border-bottom: var(--d) solid #0008;
  background: #9CC4E4; 
}
```

We can improve the code by introducing more variables to control the angle and the perspective. A good use case for modern CSS features such as `if()`, `@property`, math functions, etc.

{% image "./image.png", "CSS-only 3D boxes" %}

```css
@property --_i {
  syntax: "<number>";
  inherits: false;
  initial-value: 0; 
}
.box {
  --d: 30px;  /* the depth */
  --a: 45deg; /* the angle */
  --p: 1.2;   /* the perspective */
  
  --_a: mod(var(--a),360deg);
  --_i: round(down,var(--_a)/90deg);
  --x: abs(cos(var(--_a))*var(--d));
  --y: abs(sin(var(--_a))*var(--d));
  corner-shape: bevel;
  border-style: solid;
  border-color: #0002 #0004 #0008 #0004;
  background: #9CC4E4;
  border-width: if(
     style(--_i: 0): 0 0 var(--x) var(--y);
     style(--_i: 1): var(--x) 0 0 var(--y);
     style(--_i: 2): var(--x) var(--y) 0 0;
     style(--_i: 3): 0 var(--y) var(--x) 0;
    );
  border-radius: if(
     style(--_i: 0): var(--y) 0 calc(var(--p)*var(--y)) 0/calc(var(--p)*var(--x)) 0 var(--x) 0;
     style(--_i: 1): 0 calc(var(--p)*var(--y)) 0 var(--y)/0 var(--x) 0 calc(var(--p)*var(--x));
     style(--_i: 2): calc(var(--p)*var(--y)) 0 var(--y) 0/var(--x) 0 calc(var(--p)*var(--x)) 0;
     style(--_i: 3): 0 var(--y) 0 calc(var(--p)*var(--y))/0 calc(var(--p)*var(--x)) 0 var(--x);
    );
}
```

Here is an interactive demo where you can adjust the 3 variables:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="dPGGjGz" data-pen-title="3D box with modern CSS" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPGGjGz">
  3D box with modern CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

⚠️ Limited support (Chrome-only for now) ⚠️

Inspired by [codepen.io/amit_sheen/full/yyeeJKO](https://codepen.io/amit_sheen/full/yyeeJKO)