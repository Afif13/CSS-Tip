---
layout: layouts/post.njk
title: How to correctly use if() in CSS
description: Learn how to fix an issue you will often face when using if()
date: 2025-06-02
tags: posts
---

CSS is adding a new way to express conditions using an if() syntax. While it looks easy to use, there is a gotcha you should be aware of. Take the example below:

```css
.box {
  --n: 6; /* We define 6 */
  
  --f: calc(var(--n)/2); /* the result is 3 */
  background: if(style(--f: 3): red; else: green); /* We should get a red color */
}
```

The color is `red`, right? No, it's `green`! For the browser `--f` is equal to `calc(var(--n)/2)`. It doesn't perform the calculation and considers it like a string matching.


<p class="codepen" data-height="450" data-default-tab="css,result" data-slug-hash="dPoMeOB" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPoMeOB">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

This can be confusing, but the fix is quite easy. You register the custom property using `@property` and the browser will perform the calculation.

```css
@property --f {
  syntax: "<number>";
  inherits: false;
  initial-value: 0; 
}

.box {
  --n: 6; /* We define 6 */
  
  --f: calc(var(--n)/2); /* the result is 3 */
  background: if(style(--f: 3): red; else: green); /* We get a red color */
}
```

<p class="codepen" data-height="350" data-default-tab="css,result" data-slug-hash="zxGqjwm" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxGqjwm">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The registration is not required if you have no calculation and you only want an exact match like the examples below:

```css
.box {
  --f: error; 
  background: if(style(--f: error): red; else: green);
}

.box {
  --v: 0;
  background: if(style(--v: 0): red; else: green);
}
```

The same logic also applies to style queries as they utilize the same `style()` feature to define conditions.


Related article: [The Hidden Trick of Style Queries and if()](/if-trick/)