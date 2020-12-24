---
layout: post
title:  Coin Change Problem Revisited
date:   2018-12-09 07:39:32 -0800
categories: functional programming
---
I have been taking this course on [Coursera](https://www.coursera.org) called [Programming Languages](https://www.coursera.org/learn/programming-languages). It teaches the concepts behind programming languages and how they fit together. It has 3 parts - Part A, Part B and Part C. I'm currently on Part A. Part A uses [Standard ML](https://en.wikipedia.org/wiki/Standard_ML) and foucses on functional programming, which is why I'm taking the course in the frist palce: to learn functional programming. During the third week it teaches about this concept called tail call optimization, a technique many functional programming languages implement to prevent stack overflow. Program runtimes need to keep track of the environment in a stack frame while a function gets called to keep track of things like local variables. They need to hold them in place until the fuction returns. The problem arises when a function gets called recusively for a huge numbre of times. In such events stack frames grow more than memory can fit and they overflow. Hence, the term stack overflow.

In functional programming recursive calls are common and the language implementers built tail call optimization to circumvant the stack overflow issue. However, in order for a programmer to make use of tail call optimization one has to write their recursive functions with a tail call - the last step, the recursive call step needs to be by itself, that is, it has to be just a function call without any other extra logic.

Several years ago when I was learning about Python generators I wrote about the [coin change problem](/python/programming/2013/10/01/python-generators/). I did realize that when I called that Python function with a large enough amount it crashed. The reason turns out to be that Python doesn't have tail call optimization and the stack blows when it hits a certain limit. Just for my curiosity I ported that function to Standard ML. Now I can call it with pretty large numbers and it still holds up. Pretty neat.

Here is the version I ported to SML with a tail call:

{% highlight sml lineanchors %}
fun make_change(amount, coins=[1, 5, 10, 25], hand=None):


{% endhighlight %}