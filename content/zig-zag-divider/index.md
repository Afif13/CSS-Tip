---
layout: layouts/post.njk
title: Random Zig-Zag Dividers
description: Another fancy shape made possible using random()
date: 2026-11-17
tags: posts
---

Similar to the [wavy divider](/random-wavy-shapes/), here is another cool shape powered by `random()`: A zig-zag divider!

{% image "./image.png", "CSS-only zig-zag divider" %}

```css
.zig-zag {
  --n: 9;  /* if you change this, you need to add more points .. we don't have loops in CSS */
  --d: 80px; /* control the depth, can be percentage */
  
  --_r1: random(0px,var(--d)/2);
  --_r2: random(var(--d)/2,var(--d));
  
  clip-path: polygon(100% 0,0 0,
    calc(000%/var(--n))  calc(100% - var(--_r2)),
    calc(100%/var(--n))  calc(100% - var(--_r1)),
    calc(200%/var(--n))  calc(100% - var(--_r2)),
    calc(300%/var(--n))  calc(100% - var(--_r1)),
    calc(400%/var(--n))  calc(100% - var(--_r2)),
    calc(500%/var(--n))  calc(100% - var(--_r1)),
    calc(600%/var(--n))  calc(100% - var(--_r2)),
    calc(700%/var(--n))  calc(100% - var(--_r1)),
    calc(800%/var(--n))  calc(100% - var(--_r2)),
    calc(900%/var(--n))  calc(100% - var(--_r1))
  )
}
```

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="Random bottom Zig-Zag" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="emvqpQr" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a1e881-a2b5-7f32-a5c5-3db9028c9ca5">
  Random bottom Zig-Zag</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


We can adjust the code to have the zig-zag on the top:

```css
.zig-zag {
  --n: 9;  /* if you change this, you need to add more points .. we don't have loops in CSS */
  --d: 80px; /* control the depth, can be percentage */
  
  --_r1: random(0px,var(--d)/2);
  --_r2: random(var(--d)/2,var(--d));
  clip-path: polygon(100% 100%,0 100%,
    calc(000%/var(--n))  var(--_r2),
    calc(100%/var(--n))  var(--_r1),
    calc(200%/var(--n))  var(--_r2),
    calc(300%/var(--n))  var(--_r1),
    calc(400%/var(--n))  var(--_r2),
    calc(500%/var(--n))  var(--_r1),
    calc(600%/var(--n))  var(--_r2),
    calc(700%/var(--n))  var(--_r1),
    calc(800%/var(--n))  var(--_r2),
    calc(900%/var(--n))  var(--_r1)
  )
}
```

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="Random top Zig-Zag" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="myWNPJp" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a1e8a8-c2dd-7642-8c62-63478ffeb975">
  Random top Zig-Zag</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Or both top and bottom:

<p class="codepen" data-theme-id="39604" data-height="550" data-pen-title="Random zig-zag divider" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="jEBgrxB" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a1e8b8-d634-7a95-96e8-198e21bb3d79">
  Random zig-zag divider</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Until better support, you can use my online generator to get a static version: [css-generators.com/zig-zag-divider](https://css-generators.com/zig-zag-divider/)