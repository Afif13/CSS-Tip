---
layout: layouts/post.njk
title: Range Selection using Modern CSS
description: A new way to select elements in a specific range using if() and sibling-index()
date: 2025-10-02
tags: posts
---

Similar to [the dynamic `:nth-child()`](/nth-child/), we can use [if()](/inline-if/) and math functions to emulate a range selection.

Instead of: 

```css
/* select any element in the range [X Y] */
.container div:nth-child(n + X):nth-child(-n + Y) {
  background: red;
}
```

We can do:

```css
@property --g {syntax: "<integer>";inherits: true;initial-value: 0;}
.container {
  --X: ;
  --Y: ;
}
.container div {
  --g: sign((sibling-index() - var(--X) + 1)*(var(--Y) - sibling-index() + 1));
  /* when --g is equal to 1, the element is selected by :nth-child(n + X):nth-child(-n + Y) */
  background: if(style(--g: 1): red;);
}
```

Why reinvent the wheel? With this method, you can update the values of X and Y on the fly, since they are now variables! Something you cannot do using a classic selector.

{% image "./image.png", "Overview of :nth-child(n + X):nth-child(-n + Y)" %}

`n` needs to be a **positive integer** (zero included), so `(index - X)*(Y - index)` needs to be positive as well. The `sign()` function returns `1` when the result is positive and `-1` otherwise. We need to add `+ 1` to the formula to include zero: `(index - X + 1)*(Y - index + 1)`. 

In the demo below, update the `:nth-child()` selector and the variables `--X` and `--Y` with the same values to compare the selection.

⚠️ Limited support (Chrome-only for now) ⚠️

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="PwZGyeP" data-pen-title="Range selection using modern CSS" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PwZGyeP">
  Range selection using modern CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


We can also use the function notation and create something easier to use:

```css
@function --range(--X:1, --Y:1, --_g <integer>: 0) {
  --_g: sign((sibling-index() - var(--X) + 1)*(var(--Y) - sibling-index() + 1));
  result: var(--_g); 
}

.container div {
  --g: --range(3,8);
  background: if(style(--g: 1): red;);
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="azdmQNr" data-pen-title="Range selection using modern CSS" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/azdmQNr">
  Range selection using modern CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>