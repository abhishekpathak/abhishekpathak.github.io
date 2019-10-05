---
layout: post
title:  "Insertion Sort"
date:   2019-10-02
categories: blog algorithm
---

This is an important algorithm. Insertion sort closely mimics how we might sort a pack of cards.

> How do we sort a pack of cards? We pick one card and hold it in one hand. Then we pick another and place it before or after the card we are already holding. Then we pick a third card and "insert" it into its right place - before the first card, in the middle, or after the last card.

In insertion sort, we start with the second item, and "insert" it in its correct position relative to the first item. The first 2 items are now sorted. We then pick the 3rd item and repeat.

Concrete explanation and code: For the kth item, we compare it with the (k-1)th item, then the (k-2)th item, and so on, until we find the correct place where the kth item can be inserted. Once found, we "insert" it. Inserting is done typically by shifting all the items 1 place to the right - the place emptied by the kth item.

https://gist.github.com/abhishekpathak/8dad9a55c6b000ee3368b37b03c92825

Remember we said that insertion sort was important? Well, it turns out insertion sort is the only O(n^2) algorithm that is widely used in industry. There are a few reasons for this:

- it is a [stable](https://en.wikipedia.org/wiki/Category:Stable_sorts) sorting algorithm.
- it is an [online](https://en.wikipedia.org/wiki/Online_algorithm) algorithm.
- it is very efficient for semi-sorted arrays: for an array of n elements, where the maximum divergence an element can have from its "sorted" position is k, insertion sort takes O(kn) time. This reduces to O(n*n) in the worst case, but for semi-sorted arrays, k can be much smaller than n and insertion sort can run in practically O(n) time!

> Python uses something called "[Timsort](https://en.wikipedia.org/wiki/Timsort)", which uses insertion sort for smaller arrays, and merge sort for bigger ones.