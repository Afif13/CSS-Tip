---
layout: layouts/post.njk
title: Navigation menu with sliding items
description: A simple navigation menu with a cool sliding effect for the items
date: 2022-07-22
tags: posts
---

Create a simple navigation menu with a sliding effect
* Minimal HTML code
* No duplicated text
* Less than 20 CSS declarations
* Optimized with CSS variables

```html
<nav>
  <ul id="menu">
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
    <li class="active"><a href="/shop">Shop</a></li>
    <li><a href="/contact">Contact</a></li>
</ul>
</nav>
```


```css
nav {
  --c: #E5DDCB;
  --b: #524656;
  
  background: var(--b);
  display: flex;
}
ul {
  margin: 0 0 0 auto;
  padding: 0;
  display: flex;
  list-style: none;
}
ul li a {
  padding: 0 .8em;
  display: block;
  color: #0000;
  background: 
    linear-gradient(var(--c) 50%,var(--b) 0) 
    0% var(--_i,100%)/100% 200%;
  text-shadow:
    0 calc(2em - var(--_i,2em)) var(--c),
    0 var(--_i,-2em) var(--b);
  text-decoration: none;
  font: bold 30px/2em sans-serif;
  overflow: hidden;
  outline-offset: -5px;
  transition: .5s;
}
ul li a:hover,
ul li.active a{
  --_i: 0px;
}
ul li a:focus-visible{
  outline: 2px dashed var(--c);
}
ul li.active a:focus-visible {
  outline-color: var(--b);
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="qBojNeJ" data-preview="true" data-user="t_afif" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/qBojNeJ">
  CSS only menu with sliding effect</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


More detail: [css-tricks.com/cool-hover-effects-that-use-css-text-shadow](https://css-tricks.com/cool-hover-effects-that-use-css-text-shadow/)