---
layout: layouts/post.njk
title: How to correctly use if() in CSS
description: Learn how to easily fix an issue you will face when using if()
date: 2025-06-02
tags: posts
---

CSS is adding a new way to express conditions using an [if() syntax](https://github.com/w3c/csswg-drafts/issues/10064#issuecomment-2165157958). While it looks easy to use, there is a gotcha you should be aware of. Take the example below:

```css
.box {
  --n: 6; /* We define 6 */
  
  --f: calc(var(--n)/2); /* the result is 3 */
  background: if(style(--f: 3): red; else: green); /* We get a red color */
}
```

The color is `red`, right? No, it's `green`! For the browser the value of `--f` is equal to `calc(var(--n)/2)` (no calculation are made)

<p class="codepen" data-height="450" data-default-tab="css,result" data-slug-hash="dPoMeOB" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/dPoMeOB">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

This can be confusing but the fix is quite easy. You have to register the value using `@property` so the browser can perform the calculation. Otherwise, the browser will see the value as it is (It's like a string value).

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

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zxGqjwm" data-pen-title="Untitled" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxGqjwm">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

The registration is not required if there is no calculation and you want an exact matching like the below examples:

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


