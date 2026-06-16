---
layout: layouts/post.njk
title: Dynamic Node Connection (CSS-only Diagram)
description: Create a graph/diagram with different nodes and connections, all made with pure CSS
date: 2026-06-16
tags: posts
---

I shared various CSS tips showing how modern CSS can be used to create a dynamic connection between two elements. I connected [two circles with an arrow](/connected-circles-2/), a [curved line](/connected-circles-3/), a [straight line that bends](/bending-line/), etc.

{% image "./image.png", "various connections between two circles" %}

I even made a [CSS-only graph with a shortest-path algorithm](/graph-theory/).

{% image "./image1.png", "CSS-only graph" %}

We can still do more and create a diagram like the one below. It's still a graph, but this time the nodes are square elements, and the connectors can have different shapes and positions based on the node's position!

{% image "./image2.png", "CSS-only diagram with nodes and connectors" %}

Here is a demo with two elements. Drag them around and see how the connection behaves. It will try to link the closest edges of both nodes, or their centers, if the distance between them gets smaller. Yes, there is a nice transition as well.

⚠️ Chrome-only for now ⚠️

<p class="codepen" data-height="600" data-pen-title="Dynamic node connection (drag the elements)" data-preview="true" data-default-tab="result" data-slug-hash="emgBWGg" data-user="t_afif" style="height: 600px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/emgBWGg">
  Dynamic node connection (drag the elements)</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

A demo packed with modern CSS features such as Anchor Positioning, `border-shape`, `shape()`, container queries, `attr()`, `if()`, and more!

```html 
<div class="box" name="--a" ></div>
<div class="box" name="--b" ></div>

<!-- add a connection between "--a" and "--b" -->
<div class="link" x="--a" y="--b">
  ...
</div>
```

```css
.link {
  --b: 10px; /* line thickness */
  --s: 60px; /* the box sizes */
  --d: 150px; /* control the curvature of the line */

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

.link *:before,
.link *:after {
  content: "";
  position: absolute;
  inset: calc(-1*var(--b));
  border: var(--b) solid #556270;
  display: if(style(calc(sign(1cqw)*sign(1cqh)) = 0):none);
  transition: .3s linear;
}
/* control when each shape is visible based on the distance between the boxes */
.link *:before,
.link *:after {
  border-shape: if(
    style((hypot(100cqw,100cqh) < 200px)): 
      var(--shape1);
    style(((hypot(100cqw,100cqh) < 400px) or (100cqh < 200px)) and (100cqh < 100cqw)): 
      var(--shape2);
    style(((hypot(100cqw,100cqh) < 400px) or (100cqw < 250px)) and (100cqh > 100cqw)): 
      var(--shape3);
    else: 
      var(--shape4))
    padding-box;
}
/* the shapes of the lines */
.link *:before {
  --shape1: shape(from 0 0,curve to 50% 50% with 50% 50%,smooth to 100% 100%);
  --shape2: shape(from var(--s) 0,curve to 50% 50% with 50% 50%,smooth to calc(100% - var(--s)) 100%);
  --shape3: shape(from 0 var(--s),curve to 50% 50% with 50% 50%,smooth to 100% calc(100% - var(--s)));
  --shape4: shape(from var(--s) 0,curve to 50% 50% with calc(var(--s) + var(--d)) 0,smooth to calc(100% - var(--s)) 100%);
}
/* the shapes of the dots */
.link *:after {
  --shape1: shape(from calc(var(--b)/2) 0,arc by 0 .1px of calc(var(--b)/2) large,
          move to calc(100% + var(--b)/2) 100%,arc by 0 .1px of calc(var(--b)/2) large);
  --shape2: shape(from calc(var(--s) + var(--b)/2) 0,arc by 0 .1px of calc(var(--b)/2) large,
          move to calc(100% - var(--s) + var(--b)/2) 100%,arc by 0 .1px of calc(var(--b)/2) large);
  --shape3: shape(from calc(var(--b)/2) var(--s),arc by 0 .1px of calc(var(--b)/2) large,
          move to calc(100% + var(--b)/2) calc(100% - var(--s)),arc by 0 .1px of calc(var(--b)/2) large);
  --shape4: shape(from calc(var(--s) + var(--b)/2) 0,arc by 0 .1px of calc(var(--b)/2) large,
          move to calc(100% - var(--s) + var(--b)/2) 100%,arc by 0 .1px of calc(var(--b)/2) large);
}

.link b {scale: -1  1}
.link c {scale:  1 -1}
.link d {scale: -1 -1}
```

Even if the CSS looks a bit complex (I will be writing a detailed article to explain everything), the HTML structure is simple, which allows you to add as many elements/connectors as you want!

Open the demo below in full screen, drag the elements, and have fun!

<p class="codepen" data-height="650" data-pen-title="Untitled" data-preview="true" data-default-tab="result" data-slug-hash="emgBWeg" data-user="t_afif" style="height: 650px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/emgBWeg">
  Untitled</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>
