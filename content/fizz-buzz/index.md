---
layout: layouts/post.njk
title: Fizz Buzz using Modern CSS (no HTML)
description: A fun experiment using modern CSS to create the classic Fizz Buzz
date: 2025-12-06
tags: posts
---

Is it possible to create a Fizz Buzz using HTML and CSS? Yes, but what about a pure CSS version, with no HTML at all? It's doable using modern features. We can even simulate a kind of slider that shows four entries at a time.


```css
html {
  --N: 1000; /* the maximum number */
}
:is(html,body):before,
:is(html,body):after {
  counter-reset: n var(--n);
  animation: --n calc(var(--N)*1s) linear both;
  --x: sign(mod(var(--n),3)); /* 0 if divisible by 3 (1 otherwise) */
  --y: sign(mod(var(--n),5)); /* 0 if divisible by 5 (1 otherwise) */
  content: if(
     style((--x: 0) and (--y: 0)): "FizzBuzz"; /* divisible by 3 and 5 */
     style((--x: 0) and (--y: 1)): "Fizz"; /* divisible by 3 and not 5 */
     style((--x: 1) and (--y: 0)): "Buzz"; /* divisible by 5 and not 3 */
     else: counter(n); 
    );
}
@keyframes --n {to {--n: var(--N)}}
body:before {animation-delay: -1s}
body:after  {animation-delay: -2s}
html:after  {animation-delay: -3s}
```

⚠️ A Chrome-only experiment for now ⚠️

<p class="codepen" data-height="450" data-default-tab="result" data-slug-hash="zxqMRWr" data-pen-title="CSS-only Fizz Buzz (no HTML)" data-preview="true" data-user="t_afif" style="height: 450px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
      <span>See the Pen <a href="https://codepen.io/t_afif/pen/zxqMRWr">
  CSS-only Fizz Buzz (no HTML)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>


Inspired by ["Fizz Buzz"](https://susam.net/fizz-buzz-in-css.html)