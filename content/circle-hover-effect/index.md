---
layout: layouts/post.njk
title: A reveal hover effect with an expanding circle
description: A simple but nice hover effect to reveal your image
date: 2023-06-29
tags: posts
---

Add a reveal animation to your image with a simple and nice hover effect
* No extra element (only the `<img>` tag)
* No pseudo-element
* 10 CSS declarations


{% image "./image.png", "A reveal hover effect with an expanding circle" %}

```css
img {
  --s: 300px; /* size of the image*/
  
  width: var(--s);
  aspect-ratio: 1;
  border-radius: 50%;
  margin: calc(-.14*var(--s));
  outline: var(--s) solid #FFC48C;
  outline-offset: calc(var(--s)/-2);
  clip-path: inset(14.65% round 20px);
  transition: .7s;
}
img:hover {
  outline-offset: 0;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="PoxpvJr" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PoxpvJr">
  Hover Reveal Animation</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
