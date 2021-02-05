---
layout: post
title: "Jekyll Math Support"
date: 2020-09-09
---

# MathJax
Add this code to your `_layouts/default.html`
```
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
```
Then just use it like `\\(x = {-b \pm \sqrt{b^2-4ac} \over 2a}.\\)`  
\\(x = {-b \pm \sqrt{b^2-4ac} \over 2a}\\).  
For kramdown, escape the backslash on `(`, `[`:
- `\( \)` -> `\\(\\)`
- `\[ \]` -> `\\[\\]`

Only $$ works in kramdown, since $ is used too much in code.

# References
- <https://www.mathjax.org/#gettingstarted>
