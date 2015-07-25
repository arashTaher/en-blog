---
author: arashthr
comments: true
date: 2013-11-07 13:08:48+00:00
layout: post
slug: rec-set-part
title: 'Recursive problems : Set partitioning'
wordpress_id: 421
categories:
- Codes
- En
tags:
- Algorithm
- Python
- Recursion
---

There's no doubt that recursion is one the most powerful, exciting, and yet difficult approaches for problem solving and as we all know, attacking a problem by this almighty tool, requires keen mind and craftsmanship in extracting a recursive structure; a subtle perspective that can only be acquired by constant practicing. (Reminds me of Pride and prejudice, have you read it ?)

One of the problems that I faced recently, was finding all the partitions of a set. A [set partition](http://mathworld.wolfram.com/SetPartition.html) of a set S is a collection of disjoint subsets of S whose union is S. Interesting fact is that after a few struggles in set domain problems, it becomes straightforward to find a way to deal with another one of them. It's mainly in "One time choose it, one time don't" fashion.
BTW, this is my solution for this problem in Python.

[code language="python"]
# Prints partitions of set : [1,2] -> [[1],[2]], [[1,2]]
def part(lst, current=[], final=[]):
    if len(lst) == 0 :
        if len(current) == 0:
            print (final)
        elif len(current) > 1:
            print ([current] + final)
    else :
        part(lst[1:], current + [lst[0]], final[:])
        part(lst[1:], current[:], final + [[lst[0]]])[/code]
