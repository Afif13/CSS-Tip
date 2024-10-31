---
layout: layouts/post.njk
title: Select the last occurrence of an element in the whole document
description: Select the last occurrence of any element in the whole document
date: 2024-10-31
tags: posts
---

We saw [the selector for the first occurrence](/first-element-dom/) and here is the selector for the last occurrence.

```css
.target { /* Update with what you want to select (class, tag, etc) */
  &:nth-last-child(1 of &):not(:has(~ * &) *):not(:has(~ &) *):not(:has(~ * &)):not(:has(&)) {
    /* your CSS here  */
  }
}
```

The above will select the element with the class `.target` if:
* It's the last element among its siblings having the same class (`&:nth-last-child(1 of &)`) 
* It doesn't have a child with the same class (`:not(:has(&))`)
* It's not the previous sibling of an element having a child with the same class (`:not(:has(~ * &))`)
* It's not the child of an element that is the previous sibling of an element with the same class (`:not(:has(~ &) *)`)
* It's not the child of an element that is the previous sibling of an element having a child with the same class (`:not(:has(~ * &) *)`)

No need to learn it by heart. Simply update the `.target` with whatever you want.


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="GRVdQqv" data-pen-title="Last occurrence of an element in the whole document" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/GRVdQqv">
  Last occurrence of an element in the whole document</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another example using `span` as a selector:

```css
span { 
  &:nth-last-child(1 of &):not(:has(~ * &) *):not(:has(~ &) *):not(:has(~ * &)):not(:has(&)) {
    /* your CSS here  */
  }
}
```

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="yLmjvGB" data-pen-title="Last occurrence of an element in the whole document" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLmjvGB">
  Last occurrence of an element in the whole document</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>