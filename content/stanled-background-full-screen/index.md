---
layout: layouts/post.njk
title: Full screen slanted background
description: Only 2 properties to create a slanted background that extends to the edge of the screen
date: 2023-05-05
tags: posts
---

Add a slanted background to your container that extend to the edge of the screen.
* Only 2 CSS properties 🤯
* No pseudo-element
* No scrollbar issue
* One variable to control the angle

{% image "./image.jpeg", "A full screen slanted background" %}

```css
.slant {
  --a: 3deg; /* control the angle (yes it should be small) */
  
  border-image: conic-gradient(pink 0 0) fill 0//9999px;
  clip-path: 
    polygon(
      -9999px calc(tan(var(--a))*9999px),
      9999px calc(tan(var(--a))*-9999px),
      calc(100% + 9999px) calc(100% - tan(var(--a))*9999px),
      calc(100% - 9999px) calc(100% + tan(var(--a))*9999px)
    );
}
```
I know the code is scary but I will soon have an article to detail such techniques

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="zYmpdeK" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zYmpdeK">
  CSS-only full screen slanted background</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>