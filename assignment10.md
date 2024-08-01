# Data Structures and Algorithms with Python - Video Assignment - 7

**CDA 500**
**Vaibhav Bansal - 50560484**

## Video Link 1 (Top K Numbers):

https://buffalo.box.com/s/2ogfyksgpyecwddqn6v42aegbn4elt3l

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

**Solution 1 :** Loading the first k elements into the heap initializes it with a fixed number of elements. This is crucial because it sets up a baseline from which we can start comparing the rest of the elements in the array.  We use a min-heap in this algorithm. The min-heap allows us to efficiently track the smallest element among the top k elements. This is important because the root of the min-heap (the smallest element) is the element that we need to potentially replace when we find a new, larger element.


**Ques2 - How do you update the heap for k-N elements and why do you do that?**

**Solution 2 :**
Iterate Over Remaining Elements and remove the root element from min-heap using `heapq.heappop(min_heap)` and insert the new element in min-heap after comparison using `heapq.heappush(min_heap, number)`. We do this to maintain Top K Elements by ensuring that the heap always contains the largest k elements, we can efficiently find the top k elements in the array.


**Ques3 - Essentially, how does a heap help yo solve this problem?**

**Solution 3 :** A heap (specifically a min-heap) automatically keeps the smallest element at the root, which is ideal for this problem. It allows us to quickly access and replace the smallest element among the top k elements.

