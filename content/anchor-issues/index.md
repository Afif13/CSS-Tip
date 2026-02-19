---
layout: layouts/post.njk
title: Why is Anchor Positioning not working?
description: Learn the edge cases that prevent anchor positioning from working correctly
date: 2026-02-19
tags: posts
---

<style>
blockquote {
  margin-inline: auto;
  padding: 1em;
  border: 2px dashed;
  border-radius: 10px;
  font-size: 1.2em;
  width: fit-content;
  text-align: center;
}
blockquote p {
  margin: 0;
}
</style>

Anchor Positioning enables you to link any element on the page to another (an anchor). In theory, it's simple, but in practise there are edge cases where it doesn't work. It can be very frustrating, so let's clarify things! 

Let's consider the smallest CSS code that links `.element` with `.anchor`.

```css
.anchor {
  anchor-name: --anchor;
}
.element {
  position: absolute; /* OR fixed */
  position-anchor: --anchor;
  position-area: top;
}
```

Sounds easy, but based on the HTML structure and other CSS properties, the above may not work. `.element` can only find/reference the `.anchor` if the following rule is true: 

> The `.anchor` box is fully laid out before the `.element` box.

It's an ambiguous rule, right? Let's study the most common situations and determine when the rule holds true and when it does not.

## Parent-child Relation

If `.element` is a child of `.anchor`, the rule is true if no other CSS is applied to `.anchor`

```html
<div class="anchor">
  <div class="element"></div>
</div>
``` 
[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/parent-child/1.html)

Now, if you define a position for `.anchor` different from `static`, the rule is no longer true, and the code stops working.

```html
<div class="anchor" style="positon:relative | absolute | sticky | fixed">
  <div class="element"></div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/parent-child/2.html)

`.anchor` is now a containing block for `.element`, and cannot be fully laid out before `.element`. 

But if `.element` has a fixed position instead of absolute, it works again!

```html
<div class="anchor" style="positon:relative | absolute | sticky | fixed">
  <div class="element" style="position: fixed"></div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/parent-child/3.html)

`.anchor` is no longer a containing block for `.element`. The containing block is now the viewport.

`.anchor` can still be a containing block for a fixed element with other properties such as `transform`, `filter`, etc. (I am listing all of them [here](https://stackoverflow.com/a/52937920/8620333)). 

```html
<div class="anchor" style="translate: 10px 10px ">
  <div class="element" style="position: fixed"></div>
</div>
```

In this case, the rule is again false.

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/parent-child/4.html)

The same logic applies even if `.element` is not a direct child but a descendant of `.anchor`.

```html
<div class="anchor">
  <div>
    ...
     <div class="element"></div>
    ...
 </div>
</div>
 ```

If any ancestor of `.element` up to `.anchor` creates a containing block for it, then the rule is false, and `.anchor` cannot be referenced by `.element`.

## Sibling Relation

Now, both are siblings and share the same containing block.

If `.anchor` is placed before, then the rule is always true, whatever the CSS applied to `.anchor`.

```html
<div containing block for both>
  <div class="anchor"></div>
  <div class="element"></div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/sibling/1.html)

If `.anchor` is placed after, the rule is still true if no CSS is applied to it.

```html
<div containing block for both>
  <div class="element"></div>
  <div class="anchor"></div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/sibling/2.html)

We may think it won't work, but it does because non-positioned elements are laid out before positioned elements.

If you make `.anchor` positioned, it stops working.

```html
<div containing block for both>
  <div class="element"></div>
  <div class="anchor" style="position: absolute | fixed"></div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/sibling/3.html)

`z-index` cannot solve this. Only the position value and document order are relevant in this context.

Notice how I didn't specify `relative` or `sticky`, as they don't invalidate the rule. Elements with relative or sticky positions are laid out before elements with absolute or fixed positions. The below works fine:

```html
<div containing block for both>
  <div class="element"></div>
  <div class="anchor" style="position: sticky | relative"></div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/sibling/4.html)

## Random Relation

If both are randomly placed within the document, the first thing is to identify the containing block of `.element`. 

**`.anchor` and its containing block are inside the containing block of `.element`**

If `.element` is placed after, the rule is always true.

```html
<div containing block of .element>
  <div containing block of .anchor>
    <div class="anchor"></div>
  </div>
  <div>
    <div class="element"></div> 
  </div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/random/1.html)

If `.element` is placed before, the rule is only true if the containing block of `.anchor` does not have an absolute or fixed position. The following will not work:

```html
<div containing block of .element>
  <div>
    <div class="element"></div> 
  </div>
  <div containing block of .anchor style="position: absolute | fixed">
    <div class="anchor"></div>
  </div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/random/2.html)

But the following works:

```html
<div containing block of .element>
  <div>
    <div class="element"></div> 
  </div>
  <div style="position: relative">
    <div containing block of .anchor style="position: absolute">
      <div class="anchor"></div>
    </div>
  </div>
</div>
``` 

That new div with `position: relative` is the containing block of the containing block of `.anchor`. It doesn't have a position fixed or absolute, so the rule is true.

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/random/3.html)

This one is a bit tricky, but the logic is to consider the uppermost containing block between `.anchor` and the containing block of `.element`.

**`.anchor` is outside the containing block of `.element`**

```html
<div>
  <div class="anchor"></div>	
  <div containing block of .element>
    <div class="element"></div>
  </div>
</div>
```

The rule is always false. An element cannot reference an anchor outside its containing block. It doesn't matter if it's before or after in this case.

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/random/4.html)

**`.anchor` is inside the containing block of `.element`, but its containing block is outside**

This is a rare case that happens if `.anchor` has a fixed position and `.element` has an absolute position. Similar to the previous example, the rule is also false.

```html
<div containing block of .anchor>
  <div containing block of .element style="position: relative">
    <div class="anchor" style="position: fixed"></div>
    <div>
      <div class="element" style="position: absolute;"></div> 
    </div>
  </div>
</div>
``` 

[Click to see a demo](https://es-d-7889440420260220-59d18bf1b4c4dd532416992fbff85e3c.codepen.dev/random/5.html)

## Conclusion

Now, you should be able to figure out why your code is not working. A sum-up of the conditions that make the code fail:

* `.anchor` is outside the containing block of `.element` or is the containing block of `.element`.
* `.anchor` shares the same containing block as `.element`, is placed after `.element`, and has an absolute or fixed position.
* The uppermost containing block between `.anchor` and the containing block of `.element`, is placed after `.element`, and has an absolute or fixed position.


<small>I certainly didn't cover all the cases, so I may update this post at any time to keep it current.</small>