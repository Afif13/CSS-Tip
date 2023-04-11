---
layout: layouts/post.njk
title: Stick an element to the top-right corner
description: Place an element on the top-right corner of your CSS grid
date: 2022-01-13
tags: posts
---

Make an element stay at the top-right corner of your responsive grid using one instruction. 


{% image "./float.png", "A grid with an element anchored on the top right corner" %}

```css
grid-area: 1/auto/auto/-1;  
/* OR 
grid-row-start:1;
grid-column-end:-1 
*/
```

The element can be anywhere in your HTML code. 


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="OJxryBy" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OJxryBy">
  Float element to top/right corner</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>