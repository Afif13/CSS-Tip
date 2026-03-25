---
layout: layouts/post.njk
title: The Gotcha of using counter() with container
description: "counter() may behave strangely when combined with container. Learn about this small quirk"
date: 2026-03-25
tags: posts
---

Let's consider a basic usage of `counter()`:

```html
<section>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</section>
```

```css
section {
  counter-reset: n;
}
section div:before {
  content: counter(n);
  counter-increment: n;
}
```

Nothing fancy, and we get a counting inside the `<div>` elements.

[Click to see a demo](https://es-d-7733642320260327-019d249b-81e9-7fcd-8ab5-28afb8f16aae.codepen.dev)

Now, let's make the `<section>` element a container.

```css
section {
  counter-reset: n;
  container-type: inline-size; /* added */
}
section div:before {
  content: counter(n);
  counter-increment: n;
}
```

The code stops working!

[Click to see a demo](https://es-d-7733642320260327-019d249b-81e9-7fcd-8ab5-28afb8f16aae.codepen.dev/1.html)

It appears to be a bug, but it's not. By defining `container-type`, we apply a "style containment" to the element, which affects how `counter()` works. To simplify, `counter-reset` is no longer available for the descendants of the container. 

The previous code is equivalent to:


```css
section {
  /* counter-reset: n;  removed */
  container-type: inline-size; 
}
section div:before {
  content: counter(n);
  counter-increment: n;
}
```

Without `counter-reset`, there is no existing counter for `counter-increment` to increment, hence it will instantiate a new one within the pseudo-element. It's like we have the following code:

```css
section div:before {
  content: counter(n);
  counter-reset: n; /* added implicitely */
  counter-increment: n;
}
```

Each pseudo-element will have its own counter that contains `1`.

[Click to see a demo](https://es-d-7733642320260327-019d249b-81e9-7fcd-8ab5-28afb8f16aae.codepen.dev/2.html)

We can easily fix this by moving the incrementation to the `<div>` elements:

```css
section {
  container-type: inline-size; 
}
section div {
  counter-increment: n;
}
section div:before {
  content: counter(n);
}
```

[Click to see a demo](https://es-d-7733642320260327-019d249b-81e9-7fcd-8ab5-28afb8f16aae.codepen.dev/3.html)

Or by resetting the counter within the `<section>` (the container)

```css
section {
  container-type: inline-size; 
}
/* we target the first child to reset the counter once */
section div:first-child {
  counter-reset: n;
}
section div:before {
  content: counter(n); 
  counter-increment: n;
}
```

[Click to see a demo](https://es-d-7733642320260327-019d249b-81e9-7fcd-8ab5-28afb8f16aae.codepen.dev/4.html)

We can face more complex situations, but the rule is the same: "style containment" will create a scoping that prevents descendants from accessing the counter stuff defined on the container (or outside of it). 

If your counter is behaving strangely, don't forget about this quirk!

Can you figure out what the code below will produce?

```html
<section>
  <div></div>
  <div></div>
  <div style="container-type: inline-size;"></div>
  <div></div>
  <div></div>
</section>
```

```css
section {
  counter-reset: n;
}
section div:before {
  content: counter(n);
  counter-increment: n;
}
```

[Click to see a demo](https://es-d-7733642320260327-019d249b-81e9-7fcd-8ab5-28afb8f16aae.codepen.dev/5.html)

<small>Worth noting that we can also apply style containment using `contain: style | strict | content`.</small>

References: 

* [CSS Containment Module](https://www.w3.org/TR/css-contain-2/#containment-style)
* [CSS Lists and Counters Module](https://www.w3.org/TR/css-lists-3/#nested-counters)