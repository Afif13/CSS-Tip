---
layout: layouts/post.njk
title: Dynamic media/container queries using if()
description: Use modern CSS to express media queries and container queries differently
date: 2025-08-14
tags: posts
---

Similar to [the :nth-child() trick](/nth-child/), we can use [the if() condition](/inline-if/) and some calculation to implement the logic of media queries.


Instead of:

```css
.container {
  background; red;
  @media (width < 450px) {
    background: blue;
  }
}
```

We can do:

```css
@property --g {syntax: "<number>";inherits: true;initial-value: 0;}
.container {
  --g: max(0,sign(100vw - 450px));
  /*  "screen wdith" < 450px : --g = 0 
      "screen wdith" > 450px : --g = 1
  */
  background: if(style(--g: 1): blue; else: red);
}
```

Why reinvent the wheel with a more complex code? With this trick, you can easily update the `450px` on the fly, as now it's part of a calculation. Something you cannot do with a classic media query!

And since the variable `--g` follows a Boolean logic, we can use it to perform other calculations as well:

```css
@property --g {syntax: "<number>";inherits: true;initial-value: 0;}
.container {
  --g: max(0,sign(100vw - 450px));
  
  padding: calc(var(--g)*10px);
  /*  "screen wdith" < 450px : padding = 0px 
      "screen wdith" > 450px : padding = 10px
  */
}
```

Resize the screen in the below demo and see how things adjust based on the screen size without a single media query:

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="XJmzQOb" data-pen-title="Dynamic media queries with modern CSS" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/XJmzQOb">
  Dynamic media queries with modern CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


If we replace the `100vw` with another value, we can get something different than media queries. If, for example, we use `100cqw`, we can simulate container queries.

Here is the same demo, where this time the layout will adjust based on the width of the outer wrapper that you can resize:

<p class="codepen" data-height="480" data-default-tab="result" data-slug-hash="bNVYyrP" data-pen-title="Dynamic container queries with modern CSS" data-preview="true" data-user="t_afif" style="height: 480px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/bNVYyrP">
  Dynamic container queries with modern CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

⚠️ Limited support (Chrome only for now) ⚠️