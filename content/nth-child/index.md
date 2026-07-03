---
layout: layouts/post.njk
title: Dynamic nth-child() using sibling-index() and if()
description: Use modern CSS to control the arguments of nth-child() and update them on the fly
date: 2025-07-14
tags: posts
---

We can get [the index of an element using sibling-index()](https://css-tip.com/element-index/), and we can express [inline conditions using if()](/inline-if/). With both features, we can implement `:nth-child(An + B)`.

Instead of:

```css
.container div {
  background: blue;
}
.container div:nth-child(An + B) {
  background: red;
}
```

We can do:

```css
.container {
  --A: ;
  --B: ;
}
.container div {
  --n: calc((sibling-index() - var(--B))/var(--A));
  --g: if(style(--A = 0):
          calc(sign(sibling-index() - var(--B)) + 1);
        else: 
          calc(sign(var(--n) + 1) + mod(var(--n),1))
       );
  /* when --g is equal to 1, the element is selected by :nth-child(An + B) */
  background: if(style(--g = 1): red; else: blue);
}
```

What's the point, you might ask? It allows us to update the value of `A` and `B` on the fly since now they are variables! Something you cannot do using the classic selector.

{% image "./image.png", "Overview of :nth-child(An + B)" %}

`n` needs to be a **positive integer** (zero included).

* `sign(var(--n) + 1)` is equal to `1` when `--n` is **positive** and `-1` otherwise (The `+ 1` is used to include zero).
* `mod(var(--n),1)` is equal to `0` when `--n` is an **integer** and a value between `0` and `1` otherwise.

When the sum is equal to `1`, the element is selected by `:nth-child(An + B)`.

We need to handle the special case where `--A` is equal to `0` alone. In that case, the index needs to be equal to `B`, which means `sign(sibling-index() - var(--B))` is equal to `0`. We add `1` to have the same result as the previous calculation when the element is selected by `:nth-child(An + B)`.

In the demo below, update the `:nth-child()` selector and the variables `--A` and `--B` with the same values to compare the matching.

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="jEbObPN" data-pen-title="nth-child() using sibling-index() and if()" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/jEbObPN">
  nth-child() using sibling-index() and if()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


We can also use the function notation and create something easier to use:

```css
@function --nth-child(--A:1, --B:0) {
  --n: calc((sibling-index() - var(--B))/var(--A));
  --g: if(style(--A = 0):
          calc(sign(sibling-index() - var(--B)) + 1);
        else: 
          calc(sign(var(--n) + 1) + mod(var(--n),1))
       );
  result: if(style(--g = 1): 1;else: 0); 
}

.container div {
  --g: --nth-child(-2,10);
  /* --g is equal to "1" when the element is selected and "0" otherwise */
  background: if(style(--g = 1): red; else: blue);
  border-radius: calc(var(--g)*50%);
}
```

⚠️ Limited support (Chrome only for now) ⚠️

<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="PwPwayO" data-pen-title="nth-child() using sibling-index() and if() + function" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PwPwayO">
  nth-child() using sibling-index() and if() + function</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>