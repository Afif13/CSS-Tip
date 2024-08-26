---
layout: layouts/post.njk
title: Quantity queries using has() selector
description: a simple way to generate a Quantity query selector
date: 2024-08-26
tags: posts
---


<style>
  input,select {font-size: 1em}
  input[type=number] {font-family: monospace;width: 6ch}
  input[type=text] {width:150px}
</style>

Adjust the below to get your quantity query selector!

<form>Select <input type="text" value=".container"> if it has <select>
  <option value="0">Exactly</option>
  <option value="1">At least</option>
  <option value="2">At most</option>
  <option value="3" selected>Between</option>
</select> <input type="number" value="3" min=0> <span>and <input type="number" value="10" min=0></span> child elements</form>


```css
.container:has(> :nth-last-child(3):nth-child(-n + 8)) {
  /*                */
  /* your CSS here  */
  /*                */
}
```

Note: "At most N" is the same as "Between 1 and N" (0 is not included)

Related: [How many elements your container has?](/number-elements-has-selector/)

<script>

let cod = document.querySelector('code .token.selector');
let span = document.querySelector('form span')

document.querySelector('form').addEventListener('input', function() {
  let type = document.querySelector("select").value;
  let selector = document.querySelector("input[type=text]").value;
  let min = document.querySelectorAll("input[type=number]")[0].value;
  let max = document.querySelectorAll("input[type=number]")[1].value;

  if((+min < 0) || (+max < 0)) {
    document.querySelector('.language-css').style.background="url(https://assets.codepen.io/1480814/rick.webp) 50%/contain";
  } else {
    document.querySelector('.language-css').style.background="#272822"
  }

  span.style.display= "none";
  switch (type) {
    case "0":
      if(min == 0)
        cod.innerHTML = `${selector}:not(:has(*))`;
      else if(min == 1)
        cod.innerHTML = `${selector}:has(> :only-child)`;
      else
        cod.innerHTML = `${selector}:has(> :last-child:nth-child(${min}))`;
      break;
    case "1":
      if(min == 0)
        cod.innerHTML = `${selector}`;
      else 
        cod.innerHTML = `${selector}:has(> :nth-child(${min}))`;
      break;
    case "2":
      if(min == 0)
        cod.innerHTML = `_nothing_to_select_`;
      else if(min == 1)
        cod.innerHTML = `${selector}:has(> :only-child)`;
      else
        cod.innerHTML = `${selector}:has(> :last-child:nth-child(-n + ${min}))`;
      break;
    case "3":
      span.style.display= "revert";
      if (+min > +max) 
        cod.innerHTML = `_nothing_to_select_`;
      else if(min == max) {
        if(min == 0)
          cod.innerHTML = `${selector}:not(:has(*))`;
        else if(min == 1)
          cod.innerHTML = `${selector}:has(> :only-child)`;
        else
          cod.innerHTML = `${selector}:has(> :last-child:nth-child(${min}))`;
      }
      else if(min == 0) {
        if(max == 1)
          cod.innerHTML = `${selector}:is(:has(> :only-child),:not(:has(*)))`;
        else
          cod.innerHTML = `${selector}:is(:has(> :last-child:nth-child(-n + ${max})),:not(:has(*)))`;
      }
      else if(min == 1)
        cod.innerHTML = `${selector}:has(> :last-child:nth-child(-n + ${max}))`;
      else
        cod.innerHTML = `${selector}:has(> :nth-last-child(${min}):nth-child(-n + ${max - min + 1}))`;
      break
    default:
  }
});
</script>