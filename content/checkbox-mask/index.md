---
layout: layouts/post.njk
title: A simple checkbox using CSS mask
description: A simple checkbox but a nice animation using CSS mask
date: 2023-08-04
tags: posts
---

A simple design for your checkbox with a nice animation on click.
* No extra element (only the `<input>` tag)
* No pseudo-elements
* One value to control the size
* Less than 15 CSS declarations


{% image "./image.png", "CSS-only checkbox using CSS mask" %}

```css
input {
  --s: 90px; /* control the size */
  
  height: var(--s);
  aspect-ratio: 2;
  border-radius: var(--s);
  border: calc(var(--s)/10) solid #0000;
  padding: calc(var(--s)/10);
  background: 
    conic-gradient(#8FBE00 50%,#CC333F 0) /* the colors here */
     border-box var(--p,left)/200%;
  mask:
    radial-gradient(50% 50%,#000 98%,#0000) no-repeat
     var(--p,left)/calc(3*var(--s)/5) content-box,
    linear-gradient(#000 0 0) padding-box,
    linear-gradient(#000 0 0);
  mask-composite: add, exclude;
  transition: .5s;
  appearance: none;
}
input:checked {
  --p: right;
}
```

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="jOQdQOx" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jOQdQOx">
  CSS-only checkbox using mask</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>