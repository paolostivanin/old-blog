---
comments: true
date: 2016-03-26
layout: post
title: '[ADS] Brute Force approach and Selection Sort'
subtitle: 'In this blog post it will be explained what the brute force approach is, which algorithms and data structures use it and, lastly, the algorithm called Selection Sort will be explained'
---

It has been a long time since my last article but (finally!) I have found some time to write again. Some days ago I thought: "I'd like to brush up my algorithms and data structures knowledge so why not to write a post about every argument I will review"? And here I am, writing the first of a (very) long series of articles about this interesting and (super) important topic. What am I going to cover during the next weeks/months is written below. Of course, I will update the following schedule before finishing the last argument ;-)

#TODO complete me with data structures
* Brute Force:
    * Introduction + Selection Sort
    * Bubble Sort

* Divide and Conquer:
    * Introduction + Merge Sort
    * Quick Sort

* Decrease and Conquer:
    * Introduction + Binary Search
    * Insertion Sort
    * DFS
    * BFS
    * Direct Acyclic Graph

* [...]

The blog post will be structured as following:

 - What is algorithm/data structure X?
 - How does algorithm/data structure X works?
 - Example code in C, Python, Go and (maybe) Rust.
 
OK, enough words. Let's start with a brief introduction of what "brute force approach" means and then let's move on what the selection sort is and how it works.

Introduction
============
With the brute force approach (or exhaustive search) we go through all possible solutions extensively.\\
#TODO complete me

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
