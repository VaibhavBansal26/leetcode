# Data Structures and Algorithms with Python - Video Assignment - 7

**CDA 500**
**Vaibhav Bansal - 50560484**

<!-- ## Video Link 1 (Sliding Window Median):

https://buffalo.box.com/s/1f87a2pjqpok4w04124iax897z1hix34 -->

## Top K Numbers

**Leetcode Question Link:**

https://leetcode.com/problems/kth-largest-element-in-an-array/

## Code

```python
nums = [11, 15, 29, 2, 3, 16]
K = 3

import heapq
def top_k_numbers(nums, k):
    min_heap = []
    
    for i in range(k):
        heapq.heappush(min_heap, nums[i])
        
    for i in range(k, len(nums)):
        number = nums[i] 
        if number > min_heap[0]:
            heapq.heappop(min_heap)
            heapq.heappush(min_heap, number)
            
    return min_heap
    
top_k_numbers(nums, 4)

```

<hr/>

 - **Time Complexity :** `O(N Log K)`

 - **Space Complexity :** `O(K)`

<hr/>


## Questions

**Ques1 - Explain why you load up k elements into a heap, which heap, min or max?**

**Solution 1 :**


**Ques2 - How do you update the heap for k-N elements and why do you do that?**

**Solution 2 :**
Python's heapq module implements a min-heap, meaning the smallest element is always at the root. To simulate a max-heap using Python's min-heap, we store negative values. When inserting a number into the max-heap, we push its negative value. When retrieving the maximum value, we pop the smallest negative value


**Ques3 - Essentially, how does a heap help yo solve this problem?**

**Solution 3 :**
Balancing the heaps ensures that the size difference between the two heaps is at most one. This is crucial for efficiently finding the median.

