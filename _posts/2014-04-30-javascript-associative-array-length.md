---
layout: post
section-type: post
title: Javascript associative array length
date: '2014-04-30T08:14:02+05:30'
tags:
- javascript
- tutorial
tumblr_url: http://my-discoveries.tumblr.com/post/84316387590/javascript-associative-array-length
---
Javascript does not directly support associative array but the object notations helps it act as an associative array. The only issue is when it is an an object the array.length does not reflect the number of keys. To get the number of keys we can use the following hack. 
object.keys(associative array) gives the full array. For example
var a = [];
a.key1= 1;
a.length // 0
Object.keys(a).length //1
a[0] = 2 
Object.keys(a).length //2
