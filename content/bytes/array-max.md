---
layout: byte
title: How to find the maximum value in an array
type: bytes
tag: [JavaScript, algorithm]
description: Find the maximum value in an array.
date: 2015-05-22T00:00:00-00:00
draft: false
---
Find the maximum value in an array.

```javascript
function max(col, fn) {
  var top = -Infinity;
  var index;
  if (Array.isArray(col)) {
    for (var i = 0; i < col.length; i++) {
      var result = col[i];
      if (typeof fn === 'function') {
        result = fn(col[i]);
      } else if (typeof fn === 'string') {
        result = col[i][fn];
      }
      if (result >= top) {
        top = result;
        index = i;
      }
    }
  }
  return typeof index !== 'undefined' ? col[index] : top;
}
```

Usage:

```javascript
console.log(max([])); // -Infinity
console.log(max([2,3,1])); //  3

var col = [{n:2}, {n:3}, {n:1}];

var result = max(col, function(x) {
  return x.n;
});

console.log(result); // {n:3}

console.log(max(col, 'n')); // {n:3}
```

On github at [miguelmota/array-max](https://github.com/miguelmota/array-max).
