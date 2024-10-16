---
layout: layouts/post.njk
title: Inner display vs Outer display
description: Learn the modern way to use the display property
date: 2024-10-16
tags: posts
---

Do you know that the below declarations are the same?

```css
element {
  /* old way (always supported for backward compatibility) */
  display: inline-grid;
  /* new way */
  display: inline grid;
  display: grid inline;
  /* The two values correspond to the
     Outer display: I am seen as an "inline" element from the outside
     Inner display: I create a "grid" layout inside me
  */
}
```

The display property can take two values in any order:
- The Outer display tells how the element is seen from the outside
- The Inner display tells what kind of layout the element will generate (flexbox, grid, table, etc)


You may ask why making the display property complex?

The reason is simple: If in the future we add new layouts, we don't have to define two values ("x", "inline-x") but only one value ("x")

A masonry layout? We define `masonry` and we use `display: inline masonry` and `display: block masonry`

More detail: [Using the multi-keyword syntax with CSS display](https://developer.mozilla.org/en-US/docs/Web/CSS/display/multi-keyword_syntax_of_display)