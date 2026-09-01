---
layout: layouts/post.njk
title: Get Grid Information using pure CSS II
description: Retrieving the position of randomly placed items using only CSS
date: 2026-09-01
tags: posts
---

Extending [the previous implementation](/grid-information/) to consider a responsive grid with a random configuration. Each item can span multiple rows/columns and get placed anywhere on the grid. 

Whatever the placement, we can retrieve the position of each item using pure CSS. A task made possible using Scroll-Driven animations!

{% image "./image.png", "Getting grid information using pure CSS" %}

Here is an interactive demo where each item shows all the information it gets (number of columns, number of rows, position, index/number of items). Resize the demo and see how all the values adjust in real time.

⚠️ (Chromium-only for now) ⚠️

<p class="codepen" data-height="700" data-pen-title="Grid information (chrome-only)" data-preview="true" data-default-tab="result" data-slug-hash="RNpWpaG" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RNpWpaG">
  Grid information (chrome-only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

All the values are integers so it was an easy task to use counters and show them:

```css
.container > * {
  /* number of column */
  --n: ...;
  /* number of rows */
  --m: ...;
  /* column start/end */
  --col-s: ...;
  --col-e: ...;
  /* row start/end */
  --row-s: ...;
  --row-e: ...;
}
.container > *:before {
  content: "rows: " counter(m) "\A columns: " counter(n) 
     "\A grid-col: " counter(col-s) if(style(--col-e > calc(var(--col-s) + 1)): " / " counter(col-e);else: ;)
     "\A grid-row: " counter(row-s) if(style(--row-e > calc(var(--row-s) + 1)): " / " counter(row-e);else: ;);
  counter-reset: n var(--n) m var(--m) 
    col-s var(--col-s) col-e var(--col-e)
    row-s var(--row-s) row-e var(--row-e);
}
.container > *:after {
  content: counter(i) "/" counter(n);
  counter-reset: i sibling-index() n sibling-count();
}
```