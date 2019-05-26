---
layout: byte
title: How to find the minimum value in an array
type: bytes
tags: [JavaScript, algorithm]
description: Find the minimum value in an array.
date: 2015-05-22T00:00:00-00:00
draft: false
---
Find the minimum value in an array.

```javascript
function min(col, fn) {
  var bottom = Infinity;
  var index;
  if (Array.isArray(col)) {
    for (var i = 0; i < col.length; i++) {
      var result = col[i];
      if (typeof fn === 'function') {
        result = fn(col[i]);
      } else if (typeof fn === 'string') {
        result = col[i][fn];
      }
      if (result <= bottom) {
        bottom = result;
        index = i;
      }
    }
  }
  return typeof index !== 'undefined' ? col[index] : bottom;
}
```

Usage:

```javascript
console.log(min([])); // Infinity
console.log(min([2,1,3])); //  1

var col = [{n:2}, {n:1}, {n:3}];

var result = min(col, function(x) {
  return x.n;
});

console.log(result); // {n:1}

console.log(min(col, 'n')); // {n:1}
```

On github at [miguelmota/array-min](https://github.com/miguelmota/array-min).
