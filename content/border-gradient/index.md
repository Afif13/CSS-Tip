---
layout: layouts/post.njk
title: Border gradient with border-radius
description: The modern way to add a gradient to borders while having rounder corners
date: 2024-07-10
tags: posts
---

Save this code for the future! It's the easiest way to add a gradient coloration to borders while having rounded corners. No need for an extra element or pseudo-element and you have a transparent background!

{% image "./image.png", "CSS gradient border with border-radius" %}

```css
.gradient-border {
  border: 10px solid #0000;
  background: 
    linear-gradient(#FF4E50,#40C0CB) 
    border-box border-area;
}
```

`border-area` is a new value for `background-clip` that clips the background to the border area. As simple as that!

Here is the longhand version for more clarity:

```css
.gradient-border {
  border: 10px solid #0000;
  background-image: linear-gradient(#FF4E50,#40C0CB);
  background-origin: border-box;
  background-clip: border-area;
}
```

⚠️ Support is still limited (missing Firefox) ⚠️

<p class="codepen" data-height="300" data-pen-title="Gradient borders with rounded corners" data-preview="true" data-default-tab="result" data-slug-hash="YPNrbjz" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/YPNrbjz">
  Gradient borders with rounded corners</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

----

Until better support, you can rely on CSS mask and pseudo-element if you want transparency:

```css
.gradient-border {
  border-radius: 25px;
  position: relative;
}
.gradient-border:before {
  content: "";
  position: absolute;
  inset: 0;
  padding: 10px; /* border length  */
  background: linear-gradient(#FF4E50,#40C0CB);
  border-radius: inherit;
  mask: conic-gradient(#000) content-box exclude,conic-gradient(#000);
}
```

Or two background layers if transparency is not required:

```css
.gradient-border {
  border: 10px solid #0000;
  border-radius: 25px;
  background: 
    conic-gradient(#fff /* the background color */) padding-box,
    linear-gradient(#FF4E50,#40C0CB) border-box;
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="ZEdYKvo" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEdYKvo">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>