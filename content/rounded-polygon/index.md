---
layout: layouts/post.njk
title: Polygon shapes with rounded corners
description: Use modern CSS and Sass to generate the code of rounded polygon shapes
date: 2025-04-17
tags: posts
---

Similar to [the hexagon shape](/rounded-hexagon/), here is a generic code to create any regular polygon shape with rounded corners. Powered by Sass and the new `shape()` function.

{% image "./image.png", "CSS-only polygon shapes with rounded corners" %}


```scss
$n: 9; /* number of sides*/
$r: .2; /* control the radius [0 1] */
$a: 15deg; /* control the rotation */

$_r: 50%*math.cos(180deg/$n)/math.cos((180deg/$n*(1 - $r)));

.poly {
  aspect-ratio: 1;
  $m: ();
  @for $i from 0 through ($n - 1) {
    $c: line to;@if($i == 0){$c: from;}
    $m: append($m,$c 50% + $_r*math.cos(180deg*(2*$i - $r)/$n + $a)
                     50% + $_r*math.sin(180deg*(2*$i - $r)/$n + $a),comma);
    $m: append($m,curve to 50% + $_r*math.cos(180deg*(2*$i + $r)/$n + $a)
                           50% + $_r*math.sin(180deg*(2*$i + $r)/$n + $a)
      with 50%*(1 + math.cos($i*360deg/$n + $a))
           50%*(1 + math.sin($i*360deg/$n + $a)),comma);
  } 
  clip-path: shape(#{$m});
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="xbbxMdg" data-pen-title="Polygon shapes with rounded corners" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/xbbxMdg">
  Polygon shapes with rounded corners</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Here is another version with CSS variables in case you want to control the radius and rotation on the CSS side:

```scss
$n: 7; /* number of sides*/

.poly {
  --r: 0.25; /* control the radius [0 1] */
  --a: 10deg; /* control the rotation */
  
  aspect-ratio: 1;
  --_a: (#{180deg/$n}*var(--r));
  --_r: (50%*cos(#{180deg/$n})/cos((#{180deg/$n}*(1 - var(--r)))));
  $m: ();
  @for $i from 0 through ($n - 1) {
    $c: line to;@if($i == 0){$c: from;}
    $m: append($m,$c calc(50% + var(--_r)*cos(#{$i*360deg/$n} + var(--a) - var(--_a)))
                     calc(50% + var(--_r)*sin(#{$i*360deg/$n} + var(--a) - var(--_a))),comma);
    $m: append($m,curve to calc(50% + var(--_r)*cos(#{$i*360deg/$n} + var(--a) + var(--_a)))
                           calc(50% + var(--_r)*sin(#{$i*360deg/$n} + var(--a) + var(--_a)))
      with calc(50%*(1 + cos(#{$i*360deg/$n} + var(--a))))
           calc(50%*(1 + sin(#{$i*360deg/$n} + var(--a)))),comma);
  } 
  clip-path: shape(#{$m});
}
```

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="KwwKVZr" data-pen-title="Polygon shapes with rounded corners" data-preview="true" data-user="t_afif" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/KwwKVZr">
  Polygon shapes with rounded corners</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

⚠️ Chrome-only for now ⚠️
