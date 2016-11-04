---
comments: true
date: 2016-04-06
layout: post
tags: [ads, selection-sort, brute-force]
title: '[ADS] Brute Force approach and Selection Sort'
subtitle: 'Brute Force approach and Selection Sort algorithm explained'
---

It has been a long time since my last article but (finally!) I have found some time to write again. Some days ago I thought: "I'd like to brush up my algorithms and data structures knowledge so why not to write a post about every argument I will review"? And here I am, writing the first of a (very) long series of articles about this interesting and (super) important topic.\\
Time permitting, I will try to cover all the algorithms and data structures currently known. The blog post structure will be:

 - What is algorithm/data structure X?
 - How does algorithm/data structure X works?
 - Example code in C, Python and Go.
 
Ok, enough chit-chat. Let's start with something more interesting :-)


Introduction
============
A brute-force algorithm solves a problem in the most simple, direct or obvious way. As a result, such an algorithm can end up doing far more work to solve a given problem than a more clever or sophisticated algorithm might do. On the other hand, a brute-force algorithm is often easier to implement than a more sophisticated one and, because of this simplicity, sometimes it can be more efficient. Using this approach, the algorithm will go through all possible solutions extensively, one after the other, until the it finds one that is acceptable or until a pre-set maximum number of attempts is reached.\\
Algorithms that use the aformentioned approach are:
 - Selection Sort
 - Bubble Sort
 - Sequential Search
 - Brute-Force String Matching


Selection Sort
==============
The selection sort is a sorting algorithm that scans an entire list of elements to find the smallest one. It then swap it with the first unsorted element.\\
This means that for `N` elements it does `N-1` rounds. Let's see an example:

{% highlight text %}
Input:       32 29 12 (2) 18
                       ^

Iteration 1: (2) 29 12 (32) 18
              ^---------^

Iteration 2: 2 (12) (29) 32 18
                ^----^

Iteration 3: 2 12 (18) 32 (29)
                   ^-------^

Iteration 4: 2 12 18 (29) (32)
                      ^-----^
{% endhighlight %}

Complexity
-----------

||           Time            || Space |
|| :------------------------:|| :-----: |
|  Best  | Average  |  Worst | Worst |
| :------: | :--------: | :------: | :-----: |
| `O(n^2)` |  `O(n^2)`  | `O(n^2)` |  `O(1)` |



