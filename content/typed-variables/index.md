---
layout: layouts/post.njk
title: Typed CSS variables using @property
description: Upgrade your CSS variables by registring them using the @property
date: 2024-07-17
tags: posts
---

Stop defining your variables inside `:root`! 

Use the `@property` instead and create "Typed CSS Variables" 
* Easy to debug using Dev tools
* Implicit data validation
* Can be animated if the type allows it
* Available globally with a default value

Instead of doing this:

```css
/*
  We don't know the type of the variables 🤔
  Valid or invalid? We don't know! 🫣
  Hard to debug & the browser won't help you 😖
*/
:root {
  --color: #586de7;
  --size: 20px;
  --cols: 12;
}
```

Do this:

```css
/*
  Typed CSS variables! 🤩
  Easy to debug and the browser will help you 😃
*/
@property --color {
  syntax: '<color>';
  inherits: true;
  initial-value: #586de7; 
}
@property --size {
  syntax: '<length>';
  inherits: true;
  initial-value: 20px; 
}
@property --cols {
  syntax: '<integer>';
  inherits: true;
  initial-value: 12; 
}
```

----

Example of a data validation through the Dev tools. 

"darkpink" could have been a valid color. The browser will show you a warning and use the initial-value as a fallback. Without `@property`, there is no way to know the issue.


{% image "./image.png", "Dev tools CSS variables" %}