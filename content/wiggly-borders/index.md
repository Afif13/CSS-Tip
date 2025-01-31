---
layout: layouts/post.njk
title: A wiggly box (wavy borders) using CSS Mask
description: Another cool CSS shape using CSS mask and a few lines of code
date: 2025-01-23
tags: posts
---

Using the same code structure as [the wavy box](/image-wavy-borders/) to create another variation, a [wiggly box](https://css-shape.com/wiggly-box/)!
* Only one element (the `<img>` tag)
* No pseudo-elements
* Optimized with CSS Variables
* Works with gradient coloration

{% image "./image.png", "Images inside a CSS-only wiggly box" %}

```css
img {
  --s: 20px;  /* control the size of the wave */
  --w: 350px; /* preferred image width */
  
  width: round(var(--w),4*var(--s));
  aspect-ratio: 1;
  padding: calc(3.5*var(--s));
  box-sizing: border-box;
  border-radius: calc(4*var(--s));
  --_r:var(--s),#000;
  --_g:conic-gradient(#000 0 0) no-repeat 50%/;
  mask: 
    radial-gradient(var(--_r) 100%,#0000 calc(100% + 1px)) 
     0 0/calc(4*var(--s)) calc(4*var(--s)),
    var(--_g) calc(100% - 6*var(--s)) calc(100% - 6*var(--s)),
    var(--_g) calc(100% - 4*var(--s)) calc(100% - 4*var(--s)) subtract,
    radial-gradient(var(--_r) calc(100% - 1px),#0000) 
     var(--s) var(--s)/calc(2*var(--s)) calc(2*var(--s));
}
```


<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="gbYBPma" data-pen-title="Images inside wiggly boxes" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/gbYBPma">
  Images inside wiggly boxes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Here is another implementation with less gradients but no rounded corners for the image:

```css
img {
  --s: 20px;  /* control the size of the wave */
  --w: 350px; /* preferred image width */
  
  width: round(var(--w),4*var(--s));
  aspect-ratio: 1;
  border: calc(2*var(--s)) solid #0000;
  padding: calc(1.5*var(--s));
  box-sizing: border-box;
  mask: 
    radial-gradient(var(--s),#000 100%,#0000 calc(100% + 1px)) 
     0 0/calc(4*var(--s)) calc(4*var(--s)),
    conic-gradient(#000 0 0) no-repeat
     50%/calc(100% - 6*var(--s)) calc(100% - 6*var(--s)),
    radial-gradient(var(--s),#0000 calc(100% - 1px),#000) 
     var(--s) var(--s)/calc(2*var(--s)) calc(2*var(--s)) padding-box;
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="LEPqOwy" data-pen-title="Images inside wiggly boxes II" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/LEPqOwy">
  Images inside wiggly boxes II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

And another one with a different visual for the corners

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="JoPzpgV" data-pen-title="Images inside wiggly boxes III" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JoPzpgV">
  Images inside wiggly boxes III</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>