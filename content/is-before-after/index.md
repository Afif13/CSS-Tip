---
layout: layouts/post.njk
title: Why :is(::before,::after) doesn't work?
description: "Learn why the :is() selector doesn't work with pseudo-elements" 
date: 2025-09-22
tags: posts
---

The functional pseudo-class `:is()` is ideal for shortening selectors. Take the following example:

```css
.container button.large,
.container button.small {
  /* CSS */
}
``` 

We can write it using `:is()` like below:

```css
.container button:is(.large,.small) {
  /* CSS */
}
```

Following the same logic, you may be tempted to write the following selector:

```css
.container button:is(::before,::after) {
  /* CSS */
}
```

You select both pseudo-elements of `button` with one rule. Unfortunately, it won't work because pseudo-elements aren't valid within `:is()`.

<h2>What's the Reason?</h2>

Since `:is()` is often presented as a way to shorten selectors, many people think that the browser will "expand" the selector before doing the evaluation. 

So The following:

 ```css
 button:is(.large,.small) {

 }
 ```

will first get transformed into: 

 ```css
 button.large,
 button.small {
  
 }
 ```
 
 Then we select the elements. 

 While the logic appears to work for that particular case (and many others), it doesn't behave that way.

The `:is()` part is a pseudo-class that adds a condition to the selection, just like other selectors (such as class selectors, ID selectors, etc.) do. The key is to know how to read the selector, and you will understand why pseudo-elements aren't allowed:

* `*.small`: select any element having the class `.small`.
* `.small`: The universal selector is implicit; we can remove it.
* `.small::before`: Select the pseudo-element of "any element having the class `.small`"
* `:is(.small)`: Select any element that matches the selectors inside `:is()`:
    - has the class `.small`.
* `:is(.small,.large)`: Select any element that matches the selectors inside `:is()`:
    - has the class `.small`. **or** 
    - has the class `.large`.
* `button:is(.small,.large)`: Select any element that is a button **and** match the selectors inside `:is()`:
    - has the class `.small`. **or** 
    - has the class `.large`.
* `button:is(::before,::after)`: Select any element that is a button **and** match the selectors inside `:is()`.


Do you see the issue with the last selector? A button cannot match the selectors because a button cannot be a pseudo-element. The `:is()` pseudo-class is adding a condition to the selector. It's not selecting what is inside it. You cannot read it as <strong style="color:#cd333f">"select `::before` and `::after` of the button element"</strong>. You should read it as <strong style="color:#8A9B0F">"select the button element that matches the selectors inside `:is()`"</strong>. It won't work because a button cannot be a pseudo-element.

<h2>What about <code>:is(::before,::after){}</code> ?</h2>

Even if we don't have a selector before the `:is()`, the same logic apply because `:is(::before,::after)` is equivalent to `*:is(::before,::after)` which means "select any element that match the selectors inside `:is()`". It won't work because an element cannot be a pseudo-element.

You will probably find this a bit confusing and counter-intuitive, but never forget that pseudo-elements aren't allowed inside `:is()`. The same rule applies to the `:not()` and `:where()` pseudo-class.

<h2>What about <code>button:is(:active,:hover,:focus){}</code> ?</h2>

That selector is valid because it does make sense if we read it correctly: 

- Select any element that is a button **and** match the selectors inside `:is()`:
    - has the focus. **or**
    - is hovered. **or**
    - is being activated.

