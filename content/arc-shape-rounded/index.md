---
layout: layouts/post.njk
title: Arc shape with rounded edges
description: A modern way to create arc shapes with rounded edges using minimal code
date: 2025-05-20
tags: posts
---

[Previously](/arc-shape/), I used CSS mask to create an arc shape with rounded edges. Now, we can rely on the new `shape()` function that produces a more compact code and gives better rendering. A single-element implementation optimized with CSS variables.

{% image "./image.png", "CSS-only arc shape with rounded edges" %}


```css
@property --_f {
  syntax: "<number>";
  inherits: false;
  initial-value: 0; 
}
.arc {
  --v: 35; /* [0 100] */
  --b: 40px; /* thickness */
  
  --_v: min(99.99,var(--v));
  --_f: round(down,var(--_v),50);
  --_c: if(style(--_f: 0): small; else: large);
  aspect-ratio: 1;
  clip-path: shape(from top,
    arc to calc(50% + 50%*sin(var(--_v)*3.6deg)) 
           calc(50% - 50%*cos(var(--_v)*3.6deg)) of 50% var(--_c) cw,
    arc to calc(50% + (50% - var(--b))*sin(var(--_v)*3.6deg)) 
           calc(50% - (50% - var(--b))*cos(var(--_v)*3.6deg)) of 1% cw,
    arc to 50% var(--b) of calc(50% - var(--b)) var(--_c),
    arc to top of 1% cw
  );
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="pvvXJLY" data-pen-title="Arc shape with rounded edges" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/pvvXJLY">
  Arc shape with rounded edges</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another implementation using styles queries instead of inline conditions:

```css
@property --_f {
  syntax: "<number>";
  inherits: false;
  initial-value: 0; 
}
.arc {
  --v: 35; /* [0 100] */
  --b: 40px; /* thickness */
  
  --_v: min(99.99,var(--v));
  --_f: round(down,var(--_v),50);
  aspect-ratio: 1;
  display: grid;
  container-name: arc;
}
.arc:before {
  content: "";
  clip-path: shape(from top,
    arc to calc(50% + 50%*sin(var(--_v)*3.6deg)) 
           calc(50% - 50%*cos(var(--_v)*3.6deg)) of 50% var(--_c,large) cw,
    arc to calc(50% + (50% - var(--b))*sin(var(--_v)*3.6deg)) 
           calc(50% - (50% - var(--b))*cos(var(--_v)*3.6deg)) of 1% cw,
    arc to 50% var(--b) of calc(50% - var(--b)) var(--_c,large),
    arc to top of 1% cw
  );
  @container style(--_f: 0) {--_c: small}
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="xbboGaO" data-pen-title="Arc shape with rounded edges" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xbboGaO">
  Arc shape with rounded edges</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

