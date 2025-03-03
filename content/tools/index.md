---
layout: layouts/base.njk
title: CSS Tools
description: A collection of tools to easily generate your CSS code.
eleventyNavigation:
  key: Tools
  order: 2
---

<style> 
  ul.tools {
    padding: 0;
    list-style: none;
  }
  ul.tools a {
    text-decoration: none;
    display: grid;
    grid-auto-flow: column;
    justify-content: start;
    align-items: center;
    gap: .5em;
    font-size: 1.3em;
    font-weight: 700;
    text-transform: capitalize;
    margin-block: 1em;
  }
  ul.tools a img {
    width: 170px;
    aspect-ratio: 2;
    margin: 0;
  }
  ul.tools a p {
    text-wrap: balance;
    margin: 0;
  }
</style>

<h1>Tools for CSS code</h1>


A collection of CSS Tools to easily generate a modern & optimized code in no time.

<ul class="tools">
  <li>
    <a href="https://css-generators.com/custom-borders/">
      {% image "./custom-borders.png", "CSS custom borders" %}
      <p>Generator for custom borders<br> (Zig-Zag, Wavy, Rounded)</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/custom-corners/">
      {% image "./custom-corners.png", "CSS custom corners" %}
      <p>Generator for custom corners<br> (Scooped, Beveled)</p>
    </a>
  </li>
  <li>
    <a href="https://css-loaders.com/">
      {% image "./loaders.png", "CSS loaders" %}
      <p>Collection of CSS loaders<br> (more than 600 animations)</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/section-divider/">
      {% image "./section-divider.png", "CSS section divider" %}
      <p>Generator for section divider<br> (Triangular, Circular, Slanted)</p>
    </a>
  </li>
  <li><div id="inline-custom"></div></li>
  <li>
    <a href="/quantity-queries/">
      {% image "./quantity-query.png", "CSS quantity queries" %}
      <p>Quantity queries Selectors</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/triangle-shapes/">
      {% image "./triangles.png", "CSS triangles" %}
      <p>Collection of triangle shapes</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/ribbon-shapes/">
      {% image "./ribbons.png", "CSS ribbons" %}
      <p>Collection of ribbons<br> (more than 100 shapes)</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/starburst-shape/">
      {% image "./starburst.png", "CSS starburst" %}
      <p>Generator for starburst shapes</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/polygon-shape/">
      {% image "./polygon.png", "CSS polygons" %}
      <p>Generator for polygon shapes<br> (Rhombus, Hexagon, Octagon)</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/tooltip-speech-bubble/">
      {% image "./tooltip.png", "CSS tooltip" %}
      <p>Collection of tooltip & speech bubbles<br> (more than 100 shapes)</p>
    </a>
  </li>
  <li>
    <a href="https://css-pattern.com/">
      {% image "./patterns.png", "CSS background patterns" %}
      <p>Collection of background patterns<br> (more than 150 design)</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/wavy-shapes/">
      {% image "./wavy-shapes.png", "CSS wavy shapes" %}
      <p>Generator for wavy shapes</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/flower-shapes/">
      {% image "./flowers.png", "CSS flower shapes" %}
      <p>Generator for flower shapes</p>
    </a>
  </li>
  <li>
    <a href="https://css-shape.com/">
      {% image "./shapes.png", "CSS shapes" %}
      <p>Collection of Single element CSS Shapes</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/wavy-circle/">
      {% image "./wavy-circle.png", "CSS wavy circle" %}
      <p>Generator for wavy circles</p>
    </a>
  </li>
  <li>
    <a href="https://css-generators.com/gradient-shadows/">
      {% image "./gradient-shadow.png", "CSS gradient shadow" %}
      <p>Generator for gradient shadows</p>
    </a>
  </li>
</ul>
