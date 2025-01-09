---
layout: layouts/post.njk
title: Running animations without keyframes
description: A new way to create animations without relying on keyframes
date: 2025-01-09
tags: posts
---

Using the new `@starting-style` you can create animations without using `@keyframes`. It's not a replacement for the classic way to create animations but it can be a useful CSS trick in some situations.

Here is a simple example with a rotation. I am using big values to simulate an infinite rotation.

```css
.box {
  transition: 40s linear 1s; /* duration easing delay */
  rotate: 0turn; /* To (can be removed as it's the default value) */
  @starting-style {
    rotate: -20turn; /* From */
  }
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="MYgQVbZ" data-pen-title="Infinite rotation without keyframes" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/MYgQVbZ">
  Infinite rotation without keyframes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


Here is a more generic example where I animate one variable and then use it within different properties

```css
@property --i {
  syntax: "<number>";
  inherits: false;
  initial-value: 1000; /* To */
}
.box {
  background: hsl(calc(var(--i)*10) 80% 50%);
  translate: 0 calc(sin(var(--i))*20px);
  rotate: calc(clamp(0,mod(var(--i),10) - 5,1)*90deg);

  transition: --i 120s linear 1s; /* duration easing delay */
  @starting-style {
    --i: 0; /* From */
  }
}
```

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="OPLQvjz" data-pen-title="Complex animation without keyframes" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OPLQvjz">
  Complex animation without keyframes</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

Again, I am not saying it's better than an `animation` combined with `keyframes`. It's just a different way to express animations.