---
layout: layouts/post.njk
title: Get the index of an element within its parent
description: A native CSS function to get the index of an element among its siblings within a parent element
date: 2025-07-10
tags: posts
---

With CSS, you can use the new `sibling-index()` function to get the position of any element relative to all its sibling elements. You can also rely on `sibling-count()` to get the number of siblings.

The results are also available within pseudo-elements.

```html
<div class="container">
  <div></div>
  <div></div>
  <div></div>
  ...
</div>
```

```css
.container div { 
  border: calc(sibling-index()*2px) solid;
}
.container div::before {
  content: counter(i) "/" counter(N);
  counter-reset: N sibling-count() i sibling-index() /* they refer to the div element */
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="pvjowwj" data-pen-title="sibling-index() / sibling-count()" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/pvjowwj">
  sibling-index() / sibling-count()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

The functions are a bit verbose, so we can create our custom functions and write less code.

```css
@function --N() {
  result: sibling-count();
}
@function --i() {
  result: calc(sibling-index() - 1); /* we can change and start from 0 instead of 1 */
}

.container div { 
  border: calc(--i()*2px) solid;
}
.container div::before {
  content: counter(i) "/" counter(N);
  counter-reset: N --N() i --i() 
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="EaVxmrK" data-pen-title="sibling-index() / sibling-count() + custom functions" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/EaVxmrK">
  sibling-index() / sibling-count() + custom functions</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


⚠️ Limited support (Chrome only for now) ⚠️