---
comments: true
date: 2016-01-12
layout: post
title: '[Algorithms] Intro and Selection Sort'
subtitle: 'What is the brute force approach? What is the selection sort and how does it work?'
---

It has been a long time since my last article but (finally!) I've found some spare time to write this one.\\
Some days ago I thought: "I'd like to brush up my algorithms and data structures knowledge so why not to write a post about every argument I will review?"\\
And here I am, writing the first of a long series of articles about this interesting and (very!) important topic.\\
The following schedule contains only some of the arguments that I'm gonna cover during the next months:

* Brute Force:
    * Introduction
    * Selection Sort
    * Bubble Sort

* Divide and Conquer:
    * Introduction
    * Merge Sort
    * Quick Sort

* Decrease and Conquer:
    * Introduction
    * Binary Search
    * Insertion Sort
    * DFS
    * BFS

* [...]

Ok, enough words. Let's start with a brief introduction of what "brute force approach" means and then let's move on what the selection sort is and how it works.

Selection Sort
==============
With the brute force approach (or exhaustive search) we go through all possible solutions extensively.\\
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
