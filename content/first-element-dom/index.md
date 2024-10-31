---
layout: layouts/post.njk
title: Select the first occurrence of an element in the whole document
description: Select the first occurrence of any element in the whole document
date: 2024-10-30
tags: posts
---

A CSS selector to select the first occurrence of an element regardless of its position in the document. The equivalent of `document.querySelector('.target')`.

```css
.target { /* Update with what you want to select (class, tag, etc) */
  &:nth-child(1 of &):not(:has(&) ~ * *):not(:has(&) ~ *):not(& ~ * *):not(& *) {
    /* your CSS here  */
  }
}
```

The above will select the element with the class `.target` if:
* It's the first element among its siblings having the same class (`&:nth-child(1 of &)`) 
* It's not the child of an element with the same class (`:not(& *)`)
* It's not the child of an element that is preceded by an element with the same class (`:not(& ~ * *)`)
* It's not preceded by an element having an element with the same class (`:not(:has(&) ~ *)`)
* It's not the child of an element that is preceded by an element having an element with the same class (`:not(:has(&) ~ * *)`)

No need to learn it by heart. Simply update the `.target` with whatever you want.

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="yLmKdZo" data-pen-title="First occurence of an element in the whole document" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/yLmKdZo">
  First occurence of an element in the whole document</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Another example using `span` as a selector:

```css
span { 
  &:nth-child(1 of &):not(:has(&) ~ * *):not(:has(&) ~ *):not(& ~ * *):not(& *) {
    /* your CSS here  */
  }
}
```

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="jOgxEzz" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jOgxEzz">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>