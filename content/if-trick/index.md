---
layout: layouts/post.njk
title: The Hidden Trick of Style Queries and if()
description: Learn the secret behind the new conditions and how to use them correctly
date: 2026-02-25
tags: posts
---

With modern CSS, we have two new ways to express conditions: inline `if()` and style queries. Their syntax is as follows:


```css
/* inline if() */
.box {
  background: if(style(--n: 3): red; else: green);
}
/* style queries */
.box {
  background: green;
  @container style(--n: 3) {
    border-color: red;  
  }
}
```

The common part between them is the `style()` part, which is defined to behave the same with both features. It contains the condition that evaluates to either true or false. Most of the online demos will show you the above version, but there is another valid syntax using `=`

```css
/* inline if() */
.box {
  background: if(style(--n = 3): red; else: green);
}
/* style queries */
.box {
  background: green;
  @container style(--n = 3) {
    border-color: red;  
  }
}
```

You may intuitively think that both are equivalent, but they are not!

When using `style(--n: 3)` we are relying on the following syntax `style(<style-feature-name>: <style-feature-value>)` (called `<style-feature-plain>`). In this case, the condition evaluates to true if the computed value of the given property matches the given value (which is also computed).

Let's take the following example:

```css
.box {
  --n: calc(6/2);

  background: if(style(--n: 3): red; else: green);
}
```

What is the computed value of `--n`? 3? No, it's `calc(6/2)`. The browser doesn't perform the calculation in this context, hence the computed value is `calc(6/2)`. That value doesn't match `3` and the condition is false (we get a green color). I know, it's a bit strange, but you can see it as a string matching. 

The following will work fine:

```css
.box {
  --n: calc(6/2);

  background: if(style(--n: calc(6/2)): red; else: green);
}
```

Same as the following:

```css
.box {
  --s: new;

  background: if(style(--s: new): red; else: green);
}
```

When using `style(--n = 3)` we are relying on the following syntax `style(<style-range-value> <mf-comparison> <style-range-value>)` (called a `<style-range>`). Then we do the following steps to evaluate the condition:

1. If `<style-range-value>` is a custom property, it needs to be substituted as if the custom property was wrapped inside a `var()`.
2. Parse `<style-range-value>` to `<number>`, `<percentage>`, `<length>`, `<angle>`, `<time>`, `<frequency>` or `<resolution>`. If this cannot be done, evaluate to false.
3. If each `<style-range-value>` from the range have the same type, compute each and evaluate the comparison.

Let's apply this to our example by replacing `:` with `=`

```css
.box {
  --n: calc(6/2);

  background: if(style(--n = 3): red; else: green);
}
```

We do the substitution to get `style(calc(6/2) = 3)`. We do the parsing, and we can see both are `<integer>` (here we perform the calculation). They have the same type and are equal so the condition is true!

Let's try the other example:

```css
.box {
  --s: new;

  background: if(style(--s = new): red; else: green);
}
```

The substitution gives `style(new = new)`. The parsing will .. fail! `new` is none of the listed types, so the condition is false.

Here is a demo showing all the conditions together:

<p class="codepen" data-height="400" data-pen-title="The hidden trick of if()" data-preview="true" data-default-tab="css,result" data-slug-hash="azZrBxN" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/azZrBxN">
  The hidden trick of if()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

And the same using style queries

<p class="codepen" data-height="400" data-pen-title="The hidden trick of style queries()" data-preview="true" data-default-tab="css,result" data-slug-hash="RNGwvJm" data-user="t_afif" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/t_afif/pen/RNGwvJm">
  The hidden trick of style queries()</a> by Temani Afif (<a href="https://codepen.io/t_afif">@t_afif</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://public.codepenassets.com/embed/index.js"></script>

As a conclusion, here is what you need to remember:

* The use of `style(--variable: value)` will perform an exact match of both computed values. This one is suitable for string-like matching (ex: `style(--stock: low)`)

* `style(--variable = value)` will perform a numerical comparison between two values that should have the same type (from the types I listed previously).  This one is suitable for math stuff (ex: `style(--n = 5)`)


The first method has another interesting behavior when combined with `@property`. Learn more about this case here: [How to correctly use if() in CSS](/inline-if/).