---
layout: layouts/post.njk
title: Full-bleed layout with modern CSS
description: A few lines of code to make a section extend to the edges of the screen
date: 2024-11-26
tags: posts
---

Use modern CSS and a few lines of code to create a full-bleed layout. 

**Full-bleed**? It's when an element needs to bleed outside the main container and extend to the edge of the page.


{% image "./image.png", "CSS-only zig-zag borders" %}

```css
html {
  container-type: inline-size;
}
main {
  --w: 600px; /* the max-width */
  --m: 1em;   /* margin on small screen */
  
  margin-inline: max(   var(--m),50cqw - var(--w)/2);
}
.full-bleed {
  margin-inline: min(-1*var(--m),var(--w)/2 - 50cqw);
}
```

Another more-compact syntax 

```css
html {
  container-type: inline-size;
}
main {
  --_m: max(1em,50cqw - 600px/2);
  margin-inline: var(--_m);
}
.full-bleed {
  margin-inline: calc(-1*var(--_m));
}
```


<p class="codepen" data-height="400" data-default-tab="result" data-slug-hash="vEBBoWj" data-pen-title="Full-bleed layout with modern CSS" data-preview="true" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/vEBBoWj">
  Full-bleed layout with modern CSS</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Check the following to understand why `margin-inline` and `max()`: ["max-width + centering with one instruction"](/center-max-width/)

----

Here are other variations with different margin behaviors

```css
html {
  container-type: inline-size;
}
main {
  --w: 600px; /* the max width*/
  --m: 1em;   /* minimum margin */
  
  margin-inline: max(var(--m),50cqw - var(--w)/2);
}
.full-bleed-2 {
  margin-inline: min(-1*var(--m),var(--w)/2 - 50cqw + var(--m));
}
.full-bleed-3 {
  margin-inline: min(0px        ,var(--w)/2 - 50cqw);
}
.full-bleed-4 {
  margin-inline: min(0px        ,var(--w)/2 - 50cqw + var(--m));
}
```

Resize the below demo to see the difference

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="PwYYMRX" data-pen-title="Full-bleed layout variations" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/PwYYMRX">
  Full-bleed layout variations</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>