---
title: "Technical Interview Preparation Guide"
draft: false
showToc: true
description: I used to have some cheat sheets around to prepare myself for any incoming technical interview, so I thought it would be a better idea to gather them here for a quicker access.
date: 2021-06-13
slug: technical-interview-preparation-guide
---

# Introduction
I used to have some cheat sheets around to prepare myself for any incoming technical interview, so I thought it would be a better idea to gather them here for a quicker access.
It could help someone else to prepare quickly as well!

***Important Notes:***
> - ***This work will be always an in-progress work, I will keep updating this guide as I find any relevant materials***.
> - The order might not be so relevant. Pick and choose what you need to review.

---

# Long Term Preparation Kit

If I can afford only one book to prepare for my technical interviews, I will definitely buy the [Cracking the Coding Interview](https://www.crackingthecodinginterview.com) book by Gayle McDowell, 6th edition.
That's it, good luck!

---

# Short Term Preparation Kit

If I don't have a long time to prepare, or if I already went through the long term perpetrate kit before, and I want a quick reference, I would follow this kit.
Multiple resources and steps are already summarizing some topics from the Cracking the Coding Interview book I referred above, slightly updated by me.

**Video Kit:**
If I have a little more time, I would go through [this playlist](https://www.youtube.com/playlist?list=PLOuZYwbmgZWXvkghUyMLdI90IwxbNCiWK) first, at least once.

---

## Keep in Mind

Keep these data structures, algorithms, and concepts in mind:

- Data Structures:
    1. Linked Lists
    1. Trees, Tries, and Graphs
    1. Stacks and Queues
    1. Heaps
    1. Vectors and Array Lists
    1. **>> Hash Tables <<** (Dictionaries, Maps, ...)
    
- Algorithms:
    1. Breadth-First Search
    1. Depth-First Search
    1. Binary Search
    1. Merge Sort
    1. Quick Sort
    
- Concepts:
    1. Memory (Stacks VS Heaps)
    1. Recursion
    1. Dynamic Programming
    1. Big O Time & Space
    1. Bit Manipulation


---

## 7 Steps to Solve Algorithm Problems

1. Listen (& ask!).

1. Pick an example which is:
    1. Big (enough)
    1. Is not a special case 

1. Use a brute-force approach (at least to think of the problem).

1. Optimize your solution.

1. Walk through your algorithm and know exactly what you are going to do before starting to code, think of needed variables and data structures for instance.

1. Code! Make sure to have a:
    1. (Consistent) code style: use descriptive variable names, and you may refer for them with abbreviations later.
    1. Modular code: before coding, not after.
    
1. **TEST**!
    1. Don't use your original example.
    1. Analyze (line by line).
    1. Test with a:
        1. Small test case.
        1. Edge test case.
        1. Big test case.
    1. Test your code, not your algorithm!
    1. Think before fixing bugs (so that you won't introduce new bugs, or make the code missy or hard).
    1. Don't panic, you might not solve it from the first round.
    
---

## 3 Algorithm Strategies

1. B.U.D.
   - Go through your brute-force or best solution right now and look for:
        1. **B**ottlenecks
        1. **U**nnecessary Work
        1. **D**uplicated Work
1. Space & Time Tradeoffs
   - Always have **hash tables** at the top of your mind
1. D.I.Y. (Do it Yourself)
    - Try to solve it in your mind, and write a code that behaves the same.
    - Use a large and generic example.
    - Reverse engineering your thoughts!

---

## Bit Manipulation in a Nutshell

* Get the i*th* bit of x ==> `x & (1 << i)`
* Set the i*th* bit of x ==> `x | (1 << i)`
* Clear the i*th* bit of x ==> `x & ~(1 << i)`


---

## Linked Lists VS Arrays

| Case # | Operation / Data Structure | Arrays | Linked Lists |
|------- |--------------------------- |------- |------------- |
| 1 | get (retrieve) | Constant | Linear |
| 2 | insert and delete (@ start) | Linear | Constant |
| 3 | insert and delete (@ end) | Constant | Linear |

**Clarifications:**
* Case #1
    - An array will get any item by index in a constant `O(1)` time.
    - A linked list need to traverse and count nodes till reaching the needed item and return it, so that it needs a linear `O(n)` time.

* Case #2
    - An array will access the needed index in a constant `O(1)` time and add or delete it, but it needs a linear `O(n)` to shift **all** the old nodes to right in the case of adding and to left in the case of removing.
    - A linked list need to traverse a **few** nodes (since we will add or delete from the start), add or delete the new node and update the pointers, so it needs a constant `O(1)` time.
    
* Case #3
    - An array will access the needed index in a constant `O(1)` time and add or delete it, and since we are adding or deleting from the end, it needs a constant `O(1)` to shift the **few** old nodes to right in the case of adding and to left in the case of removing.
    - A linked list need to traverse **almost all** nodes (since we will add or delete from the end), add or delete the new node and update the pointers, so it needs a linear `O(n)` time.
    

---

## Sort Algorithms

| Algorithms | Average Time Complexity | Worst Time Complexity | Worst Space Complexity | Keys / Notes |
|----------- |------------------------ |---------------------- |----------------------- |---------------- |
| **Best Time:**
| Quick Sort | O(n lg n) | O(n^2) | O(lg n) | Pivot could make things missy |
| Merge Sort | O(n lg n) | O(n lg n) | O(n) | Divide and conquer |
|
| **Best Space:**
| Bubble Sort | O(n^2) | O(n^2) | O(1) *in-place* | Compare every pair and swap if they are not in order |
| Insertion Sort | O(n^2) | O(n^2) | O(1) *in-place* | Compare every item with all previous items, if a smaller (a larger) item is found, move all items in between to right and *insert* that item in the correct place. |
| Selection Sort | O(n^2) | O(n^2) | O(1) *in-place* | Find the smallest (largest) item and add it to the end of the sorted part. Usually worse than insertion sort. *The first part is always sorted*. |


* Lower bound for sorting algorithms is O(n lg n).

---

## Search Algorithms

| Algorithm | Average / Worst Time Complexity | Average / Worst Space Complexity | Why to use? | Notes |
|---------- | ------------------------------- |--------------------------------- |------------ |------ |
| Binary Search | O(lg n) | O(lg n) | *Best time* | **Works with sorted data only**. Extra space is needed for the call stack in the recursive solution. |
| Linear Search | O(n) | O(1) *in-place* | *Best space* | Works with any (sorted or unsorted) data. |

---

# Sources and References
- [Cracking the Coding Interview](https://www.crackingthecodinginterview.com). A book by Gayle McDowell, 6th edition.
