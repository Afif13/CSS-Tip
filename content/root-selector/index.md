---
layout: layouts/post.njk
title: The shortest selector for the root element
description: Only one charater is need to target the html element
date: 2024-05-06
tags: posts
---

To target the `html` element, you either use "`html{}`" or "`:root{}`" but thanks to CSS nesting you can simply use "`&{}`"

When used alone, the nesting selector will match the root element! 

A one-character selector 🤯

⚠️ It has a lower specificity than html and :root


```css
& {
  font-family: sans-serif;
  background: #25fca4;
  --variable: value;
  /* and so on */
}
/* same as html {} and :root {} 
   with a lower specificity! 
*/
```
