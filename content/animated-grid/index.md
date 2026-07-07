---
layout: layouts/post.njk
title: Responsive CSS Grid Layout with Animation
description: A responsive grid with a smooth animation when the layout is updated
date: 2026-07-07
tags: posts
---

Inspired by [the demo of Bramus](https://codepen.io/bramus/pen/ogBYjgm), I implemented an animated grid layout. On resize, the elements get a nice animation as they move to their new positions. You can even add or remove items, and everything will adjust smoothly as well.

Try it!

⚠️ (Chromium only for now) ⚠️

<p class="codepen" data-height="750" data-pen-title="Animated grid layout on resize" data-preview="true" data-default-tab="result" data-slug-hash="bNgamKV" data-user="t_afif" style="height: 750px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bNgamKV">
  Animated grid layout on resize</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


The main idea is to calculate the coordinates of each item within the grid, and instead of relying on the automatic placement, I place them using `translate`. When the layout is updated, all coordinates change, which in turn updates the translate values. We can apply a transition to the translate property to get a nice effect!

```css
.container {
  --g: 10px; /* gap */
  --s: 130px; /* image size */
  
  display: grid;
  container-type: inline-size;
}
.container > * {
  grid-area: 1/1;
  width: var(--s);
  aspect-ratio: 1;
  /* The number of columns */
  --n: round(down,(100cqw + var(--g))/(var(--s) + var(--g)));
  /* The coordinates */
  --i: round(down,(sibling-index() - 1)/var(--n));
  --j: mod(sibling-index() - 1,var(--n));
  translate: 
    calc(var(--j)*(100% + var(--g))) 
    calc(var(--i)*(100% + var(--g)));
  transition: .4s,scale .3s .4s,opacity .3s .3s,rotate .3s .3s;
  /* the entry effect when adding a new item */
  @starting-style {
    scale: 0;
    opacity: 0;
    rotate: -1turn;
  }
}
```