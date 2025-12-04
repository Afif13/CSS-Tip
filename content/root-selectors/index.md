---
layout: layouts/post.njk
title: The Hidden Selectors of The HTML Element
description: Discover alternative selectors for the html element beyond the classic `:root{}` and `html{}`
date: 2025-12-04
tags: posts
---

How would you select the `<html>` element? Using the classic and well-known `html {}` and `:root {}` selectors, right? What if I tell you there are other hidden selectors.

I will start with [the shortest selector for the root element](/root-selector/), the nesting selector. A one-character selector:


```css
& {
  font-size: 20px;
  background: lightblue;
}
```

The next one is the `:scope` selector

```css
:scope {
  font-size: 20px;
  background: lightblue;
}
```

For those selectors, I am relying on their fallback behavior. The nesting selector `&` will behave the same as `:scope` when not used inside a nested rule and `:scope` represents the root of the document when there is no scoping root.

The `<html>` element is the only element having `head` and `body` as child elements, so we can use the `:has()` selector like below:

```css
:has(head) {
  font-size: 20px;
  background: lightblue;
}
/* OR  */
:has(body) {
  font-size: 20px;
  background: lightblue;
}
```

The `<html>` element is the only element without a parent, so here is another fancy selector using `:not()`

```css
:not(* *) {
  font-size: 20px;
  background: lightblue;
}
```

Let's add the child combinator (`>`) to have two eyes and a nose!

```css
:not(* > *) {
  font-size: 20px;
  background: lightblue;
}
```

We can also have more combinations like below:

```css
:is(&) {}
:where(&) {}
&& {}
&&&& {} /* Yes, you can append as many "&" as you want! */
:has(> body)
:has(> head)
:has(body,head)
/* etc... */
```

Are they useful? Probably not, but it's a fun exercise to explore CSS Selectors.