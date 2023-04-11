---
layout: layouts/post.njk
title: CSS-only scrolling shadow
description: Create a scrolling shadow effect using only CSS gradients
date: 2021-11-24
tags: posts
---

Create a CSS-only Scrolling Shadow effect with a few lines of code. 
* No JavaScript 
* No extra element
* No pseudo element
* Only background properties.

{% image "./scrol.png", "CSS-only scrolling shadow" %}


```css
.scrollbox {
  overflow: auto;
  
  --g: radial-gradient(55% 20px, #0009, #0000);  
  background: 
    linear-gradient(#fff 10px, #0000 40px calc(100% - 40px),#fff calc(100% - 10px)) local, 
    var(--g) top   /100% 200%,    
    var(--g) bottom/100% 200%;
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="bGrPBLJ" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bGrPBLJ">
  CSS only Scrolling shadow</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

More detail: [How does this scrolling shadows CSS-magic work?](https://stackoverflow.com/a/59431975/8620333)