---
layout: post
title:  "The Importance of Insertion Sort"
date:   2019-10-02
categories: blog algorithms
---

![Title Image](/blog/insertion-sort.jpg)



It is easy to pile up insertion sort along with other quadratic algorithms (bubble sort, selection sort) as an inefficient sorting algorithm and something only to be glanced at before moving on to the uber-cool Quicksort. Well, it turns out that insertion sort is the only O(n²) algorithm that is widely used in industry. Just what makes it  special? Lets dive deeper.

Insertion sort closely mimics how we might sort a pack of cards.

> How do we sort a pack of cards? We pick one card and hold it in one hand. Then we pick another and place it before or after the card we are already holding. Then we pick a third card and "insert" it into its right place - before the first card, in the middle, or after the last card.

In insertion sort, we start with the second item, and "insert" it in its correct position relative to the first item. The first 2 items are now sorted. We then pick the 3rd item and repeat.

**More formally**, for the *kth* item, we compare it with the *(k-1)th* item, then the *(k-2)th* item, and so on, until we find the correct place where the *kth* item can be inserted. Once found, we "insert" it. Inserting is done typically by shifting all the items 1 place to the right - the place emptied by the *kth* item.

```python
import unittest

# insertion sort implementation
# time complexity: O(n^2)
# space complexity: O(1)
def insertion_sort(arr):
    if not arr or len(arr) <= 1:
        return arr
    for i in range(len(arr)):
        var = arr[i]
        j = i
        while j > 0 and arr[j-1] > var:
            arr[j] = arr[j-1]
            j -= 1
        arr[j] = var
        print("inserting ", var, " at position", j, " in arr ", arr)
    return arr

class Test(unittest.TestCase):

    def test_insertion_sort(self):
        input = [4, 1, 5, 1, 7, 0, 9, 2]
        output = insertion_sort(input)
        expected = [0, 1, 1, 2, 4, 5, 7, 9]
        self.assertEqual(expected, output)

unittest.main(verbosity=2)        
```
Remember we said that insertion sort was important? Going through the formal algorithm above, we begin to see a few reasons for this:
* it is a [stable](https://en.wikipedia.org/wiki/Category:Stable_sorts) sorting algorithm.
* it is an [online](https://en.wikipedia.org/wiki/Online_algorithm) algorithm. This is a big deal when you have constantly increasing data sets which is true for a lot of real life scenarios.
* it is very efficient for semi-sorted arrays: for an array of n elements, where the maximum divergence an element can have from its “sorted” position is k, insertion sort takes O(kn) time. This reduces to O(n*n) in the worst case, but for semi-sorted arrays, k can be much smaller than n and insertion sort can run in practically O(n) time! Semi-sorted arrays are a lot more common in real life than we think.

> Python uses something called "[Timsort](https://en.wikipedia.org/wiki/Timsort)", which uses insertion sort for smaller arrays, and merge sort for bigger ones.

So the next time you see insertion sort, remember to appreciate its nuances. This is what Engineering is all about.