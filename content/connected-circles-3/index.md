---
layout: layouts/post.njk
title: Connecting Circles With a Curved Line
description: Using border-shape and anchor positioning to create a connection between two circles
date: 2026-05-26
tags: posts
---

Reusing [the previous implementation](/connected-circles/) to transform the arrow shape into a curved line. The line's curve adjusts based on the distance and positions of the circles.

{% image "./image.png", "CSS-only connected circles with curved line" %}

A CSS-only implementation powered by the future of CSS (Anchor Positioning, `shape()`, border-shape, `if()`, and more).

The HTML code is still the same:

```html
<div class="circle" name="--a" ></div>
<div class="circle" name="--b" ></div>

<div class="link" x="--a" y="--b">
  <a></a><b></b><c></c><d></d>
</div>
```

And the relevant CSS code is relatively small:

```css
.link {
  --b: 10px; /* line thickness */
  --x: attr(x type(<custom-ident>));
  --y: attr(y type(<custom-ident>));
}
.link * {
  position: absolute;
  --_x: calc(anchor(var(--x) inside) + anchor-size(var(--x))/2 - .1px);
  --_y: calc(anchor(var(--y) inside) + anchor-size(var(--y))/2);
  container-type: size;
}
.link :is(a,b) {top:  var(--_x); bottom: var(--_y)}
.link :is(a,c) {left: var(--_x); right:  var(--_y)}
.link :is(c,d) {top:  var(--_y); bottom: var(--_x)}
.link :is(b,d) {left: var(--_y); right:  var(--_x)}
.link *:before {
  content: "";
  position: absolute;
  inset: calc(-1*var(--b));
  border: var(--b) solid #556270;
  opacity: calc(sign(1cqw)*sign(1cqh));
  border-shape: shape(from 0 0,curve to 50% 50% with if(
    style((100cqw < 200px) or (100cqh < 200px)): 0;
    style((100cqw > 400px)): 40%;
    else: 50%) 0,smooth to 100% 100%) padding-box;
}
.link b {scale: -1  1}
.link c {scale:  1 -1}
.link d {scale: -1 -1}
```

Drag the circles in the demo below and see how the shape of the line updates:

⚠️ Chrome-only for now ⚠️

<p class="codepen" data-height="600" data-pen-title="Connected circles with a curved line" data-preview="true" data-default-tab="result" data-slug-hash="JobrNvM" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/JobrNvM">
  Connected circles with a curved line</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

You can have as many circles/links as you want.

<p class="codepen" data-height="600" data-pen-title="Connected circles with a curved line II" data-preview="true" data-default-tab="result" data-slug-hash="OPbxmEe" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/OPbxmEe">
  Connected circles with a curved line II</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
