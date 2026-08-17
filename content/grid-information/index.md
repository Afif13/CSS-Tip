---
layout: layouts/post.njk
title: Get Grid Information using pure CSS
description: With a few lines of code, you can get the number of columns, number of rows, and item coordinates
date: 2026-08-17
tags: posts
---

Thanks to modern CSS, it's now easy to retrieve various information from a responsive CSS grid such as the number of rows, number of columns, and the coordinates of each item within the grid. The only requirement is to have equal-width columns. Rows can have different heights.

```css
.container {
  --s: 120px; /* column size */
  --g: 10px;  /* gap */
  
  display: grid;
  grid-template-columns: repeat(auto-fill,minmax(var(--s),1fr));
  gap: var(--g);
  container-type: inline-size; /* to be able to use 100cqw */
}
.container > * {
  /* number of columns */
  --n: round(down,(100cqw + var(--g))/(var(--s) + var(--g)));
  
  /* number of rows */
  --m: round(up,sibling-count()/var(--n));
  
  /* item coordinates */
  --x: round(down,(sibling-index() - 1)/var(--n)); /* row index */
  --y: mod(sibling-index() - 1,var(--n)); /* column index */
}
```

Here is an interactive demo where each item shows all the information it gets. You can resize to notice the responsive behavior where all the values adjust in real time.

⚠️ (Chromium-only for now) ⚠️

<p class="codepen" data-height="700" data-pen-title="Grid information (chrome-only)" data-preview="true" data-default-tab="result" data-slug-hash="vEgqgob" data-user="t_afif" style="height: 700px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/vEgqgob">
  Grid information (chrome-only)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


If you combine this with [the new if()](https://css-tip.com/if-trick/), you can easily create conditional styling.

Color elements in a specific row

```css
.container > * {
  background: if(style(--x = 3): red;)
}
```

Or specific column

```css
.container > * {
  background: if(style(--y = 2): red;)
}
```

Or both:

```css
.container > * {
  background: if(style((--x = 3) or (--y = 2)): red;)
}
```

<p class="codepen" data-height="600" data-pen-title="Row/columns selection" data-preview="true" data-default-tab="result" data-slug-hash="GgrbWJb" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GgrbWJb">
  Row/columns selection</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

We can have more complex conditions and combine them all:

```css
.container > * {
  background: if(
    style((--y = calc(var(--n) - 1)) and (--x = 0)): red; /* last element of first row */
    style((--x = calc(var(--m) - 1))): green; /* last row  */
    style(--x = --y): orange; /* the diagonal */
  )
}
```

<p class="codepen" data-height="600" data-pen-title="Random grid selection" data-preview="true" data-default-tab="result" data-slug-hash="rajEyxY" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/rajEyxY">
  Random grid selection</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>