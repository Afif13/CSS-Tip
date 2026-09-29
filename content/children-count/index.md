---
layout: layouts/post.njk
title: Implementing children-count() using Modern CSS
description: Using Scroll-Driven Animations to count the number of children
date: 2026-09-29
tags: posts
---

We can get the number of siblings using `sibling-count()` but we cannot get the number of children yet. There is a proposal for a [`children-count()` function](https://github.com/w3c/csswg-drafts/issues/11068), but until we get an official release, we can hack it using Scroll-Driven Animations.

First, you add an extra element inside your container (That's one drawback of the method)

```html
<div class="container">
  <!-- Your content -->
  <n></n> <!-- the extra element -->
</div>
```

Then you make its width equal to the number of siblings multiplied by `1px`

```css
.container > n {
  position: absolute;
  width: calc((sibling-count() - 1)*1px);
  /* -1 is used to exclude our extra element from the count */
}
```

Finally, we apply a trick from a previous post ([Get the width & height of any element without JavaScript](/element-dimension/)) to get the width of that element and transfer it to the parent element. 

```css
@property --_n {syntax: "<number>";inherits: false;initial-value: 0;}

.container {
  timeline-scope: --n;
  animation: --n linear both;
  animation-timeline: --n;
  animation-range: entry 100% exit; 
  --n: round(1/(var(--_n))); /* --n: children-count() */
}
@keyframes --n {0% {--_n: 1}}

.container > n {
  position: absolute;
  overflow: auto;
  width: calc((sibling-count() - 1)*1px);
}
.container > n:before {
  content: "";
  display: block;
  width: 1px;
  view-timeline: --n x;
}
```

A useful trick to display the count of some hidden content

<p class="codepen" data-theme-id="39604" data-height="450" data-pen-title="children-count() using pure CSS" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="zxZzgZX" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a0e974-4336-7659-8587-fa4863c1f22a">
  children-count() using pure CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Or to have dynamic grid layouts (inspired by [kizu.dev/tree-counting-and-random/#square-ish-layout](https://kizu.dev/tree-counting-and-random/#square-ish-layout))

<p class="codepen" data-theme-id="39604" data-height="550" data-pen-title="Square-ish layout" data-preview="true" data-version="2" data-default-tab="result" data-slug-hash="raywXoX" data-user="t_afif" style="height: 550px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/editor/t_afif/pen/01a0e9ae-af7f-713a-a828-ab688aebc94e">
  Square-ish layout</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


⚠️ A very hacky method to use with caution ⚠️