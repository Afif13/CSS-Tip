---
layout: layouts/post.njk
title: Horizontal list of stacked avatars
description: Create a list of stacked avatars with a nice hover effect
date: 2023-12-25
tags: posts
---

Create a list of stacked avatars with a cool hover effect and with transparency
* Minimal HTML (images inside a container)
* Works with any number of images
* Powered by modern CSS (CSS variables, mask, @property, has() selector and more)


{% image "./image.png", "CSS-only list of stacked avatars" %}

```css
@property --h {
  syntax: "<length-percentage>";
  initial-value: 0%;
  inherits: true;
}
@property --t {
  syntax: "<length-percentage>";
  initial-value: 0%;
  inherits: true;
}

.container {
  --s: 150px; /* image size*/
  --o: 30px;  /* the overlap */
  --g: 12px;  /* the gap */ 
  
  display: flex;
  gap: var(--g);
  padding: 3px; /* a small padding to make room for the shadow */
  clip-path: inset(0);
  transition: 0s .6s;
  filter: drop-shadow(0 0 1px #000) drop-shadow(0 0 1px #000) drop-shadow(0 0 #000) drop-shadow(0 0 #000);
}
.container img {
  height: var(--s);
  aspect-ratio: 1;
  border-radius: 50%;
  border-block: var(--s) solid #0000;
  margin-block: calc(-1*var(--s));
  translate: 0 var(--t);
  transition: --h .6s,--t .6s;
}
.container img:not(:last-child) {
  margin-right: calc(-1*var(--o));
  mask: radial-gradient(50% 50% at 
    calc(150% + var(--g) - var(--o)) calc(50% - var(--h)),
    #0000 calc(100% + var(--g)),#000 calc(101% + var(--g)))
    padding-box;
}
.container:hover {
  clip-path: inset(-999px 0 0);
  transition: 0s;
}
img:hover {
  --h: calc(-.7*var(--s));
  --t: calc(-.7*var(--s));
}
img:has(+ img:hover) {
  --h: calc( .7*var(--s));
}
```

<p class="codepen" data-height="550" data-default-tab="result" data-slug-hash="mdoyOqb" data-preview="true" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/mdoyOqb">
  Stacked Avatars with hover effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>