---
layout: layouts/post.njk
title: How many elements your container has?
description: Detect the number of elements inside a container using :has() selector
date: 2022-10-10
tags: posts
---

Use the `:has()` selector and style your container based on its number of elements (direct children)

⚠️ It doesn't count text nodes. Only tags!

```css
.container:not(:has(*)) { /* 0 elements */}
.container:has(> :last-child:nth-child(1)) { /* 1 element  */}
.container:has(> :last-child:nth-child(2)) { /* 2 elements */}
.container:has(> :last-child:nth-child(3)) { /* 3 elements */}
/*.container:has(> :last-child:nth-child(N)) { /* N elements */}*/
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="ZEomRYP" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/ZEomRYP">
  How many elements it :has()?</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

You can also have range selection

```css
.container:has(> :nth-child(3)) { /* 3 elements or more */ }
/* .container:has(> :nth-child(X)) : X elements or more */

.container:has(> :last-child:nth-child(-n + 3)) { /* between 1 and 3 elements */}
/* .container:has(> :last-child:nth-child(-n + X)): between 1 and X elements */

.container:has(> :nth-last-child(3):nth-child(-n + 3)) { /* between 3 and 5 elements */}
/* .container:has(> :nth-last-child(X):nth-child(-n + (Y - X + 1))): between X and Y elements */
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="oNVJVJq" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/oNVJVJq">
  How many elements it :has()?</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Related: [Quantity queries using has() selector](/quantity-queries/)