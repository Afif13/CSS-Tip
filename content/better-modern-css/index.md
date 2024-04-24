---
layout: layouts/post.njk
title: Write better CSS with modern CSS
description: Optimize your code and reduce redundancy using modern CSS.
date: 2024-04-24
tags: posts
---

A lot of new CSS features can help you optimize your code and reduce redundancy.
* CSS Nesting
* CSS Variables
* Media Query range features


Here is an example of a CSS code with a lot of redundancy

```css
/*
  The same selector 3 times!! 🤮
  max-width? does it mean bigger or smaller?? 🫣
  grid-template-columns everywhere !! 😬
*/
.container {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 10px;
}
@media (max-width: 800px) {
  .container {
    grid-template-columns: repeat(2,1fr);  
  }
}
@media (max-width: 400px) {
  .container {
    grid-template-columns: 1fr;  
  }
}
```

It can be optimized like below using the modern features

```css
/*
  one selector 🤩
  one property 🤩
  clear media queries 🤩
*/
.container {
  display: grid;
  grid-template-columns: repeat(var(--n,3),1fr);
  gap: 10px;
  @media (width < 800px) {
    --n: 2;
  }
  @media (width < 400px) {
    --n: 1;
  }
}
```
