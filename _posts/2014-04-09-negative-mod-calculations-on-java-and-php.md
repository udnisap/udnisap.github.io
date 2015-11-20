---
layout: post
section-type: post
title: Negative Mod calculations on Java and PHP
date: '2014-04-09T10:15:41+05:30'
tags:
- java
- bug
- mathematics
tumblr_url: http://my-discoveries.tumblr.com/post/82193564084/negative-mod-calculations-on-java-and-php
---
Today I found out that mod calculations on java is not working as it should. 
For example,  in Java world `3%5 = 3` which is correct. But `-3 % 5 = -3` but not `2` which is the correct answer.
This can be fixed via `(x % y + y) % y`