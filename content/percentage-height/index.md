---
layout: layouts/post.njk
title: A Better Way to Express Percentage Height
description: A modern alternative to the classic percentage height that always work
date: 2026-02-10
tags: posts
---

Percentage height is a common issue in CSS. Using `height: 100%` to fill the vertical space fails in most cases because the parent container doesn't have an explicit height. Even if the parent has a definite height, you may still face issues related to margin, box-sizing, etc. 

Instead of `height: 100%`, you can rely on the new `stretch` value that will do a better job!


```css
.box {
  height: stretch;
}
```

## How does it work?

As its name suggests, it will try to stretch the element to fill the parent container (more precisely the containing block).

It works following two rules:
1. If the element can be aligned using `align-self` (and `align-items`), the value produces the same result as a stretch alignment (`align-self: stretch`).
2. If alignment doesn't apply, it works the same way as `height: 100%`, expect that margin is considered and the value of `box-sizing` doesn't matter. In other words, you won't get overflow issues due to margin, padding, or border.

In the demo below, `height: 100%` will either fail or create an overflow, while `height: stretch` is perfect!

⚠️ Limited Support (Chrome-only for now)

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="pvbQQqO" data-pen-title="Height: 100% vs height: stretch" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/pvbQQqO">
  Height: 100% vs height: stretch</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Additionally, using `height: stretch` gives the element a definite height, allowing for a cascading stretch.

```css
* {
  height: stretch;
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="YPWRdzN" data-pen-title="cascading stretch" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/YPWRdzN">
  cascading stretch</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

`stretch` may not work if self-alignment doesn't apply to the element AND the parent container (containing block) doesn't have an explicit height. Similar to `height: 100%`, it will fallback to `auto`. Those cases are rare, but don't forget about them.

Here is an example involving inline-block elements.

<p class="codepen" data-height="350" data-default-tab="result" data-slug-hash="zxBMyBx" data-pen-title="No stretching" data-preview="true" data-user="t_afif" style="height: 350px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxBMyBx">
  No stretching</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## What about a percentage different from 100%?

`stretch` only covers the `100%` case, so if you want to, for example, consider `height: 80%`, you need to rely on the `calc-size()` function.

```css
.box {
  height: calc-size(stretch, .8*size);
  /* same as height: calc(.8*stretch) */
}
```

The `size` keyword in the calculation will refer to the `stretch` value to find the result, which is the same as "80% of stretch".

<p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="QwEJzGJ" data-pen-title="calc-size() with stretch" data-preview="true" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/QwEJzGJ">
  calc-size() with stretch</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Note that the same applies to `width: stretch`, expect that we consider the `justify-*` properties instead of the `align-*` ones in the first rule.