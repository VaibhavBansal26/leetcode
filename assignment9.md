# Data Structures and Algorithms with Python - Video Assignment - 6

**CDA 500**
**Vaibhav Bansal - 50560484**

## Video Link 1 (Sliding Window Median):

https://buffalo.box.com/s/1f87a2pjqpok4w04124iax897z1hix34

## Sliding Window Median

**Leetcode Question Link:**

https://leetcode.com/problems/sliding-window-median/

## Code

```python
class Solution:
    import heapq

    def __init__(self):  
        self.min_heap = []
        self.max_heap = []
        self.result = []

    def balanceHeaps(self):
        if len(self.max_heap) < len(self.min_heap):
            heapq.heappush(self.max_heap, -heapq.heappop(self.min_heap))
        elif len(self.max_heap) > len(self.min_heap) + 1:
            heapq.heappush(self.min_heap, -heapq.heappop(self.max_heap))



    def removeIndex(self, heap, removeNumber):
        idx = heap.index(removeNumber)
        last_node = heap[-1] 
        heap[idx] = last_node       
        del heap[-1]
        if idx < len(heap):
            if last_node > removeNumber:
                heapq._siftup(heap, idx)
            else:
                heapq._siftdown(heap, 0, idx)
        self.balanceHeaps()   


    def medianSlidingWindow(self, nums: List[int], k: int) -> List[float]:
        for ind, num in enumerate(nums):
            # Insert
            if not self.max_heap or num <= -self.max_heap[0]:
                heapq.heappush(self.max_heap, -num)
            else:
                heapq.heappush(self.min_heap, num)

            self.balanceHeaps()

            if (ind+1) - k >= 0:
                if len(self.max_heap) == len(self.min_heap):
                    self.result.append((-self.max_heap[0] + self.min_heap[0]) / 2)
                else:
                    self.result.append(-self.max_heap[0] / 1.0)

                removeNumber = nums[ind+1-k]
                if removeNumber <= -self.max_heap[0]:
                    self.removeIndex(self.max_heap, -removeNumber)
                else:
                    self.removeIndex(self.min_heap, removeNumber)

        return self.result

```

<hr/>

 - **Time Complexity :** `O(N Log n)`

 - **Space Complexity :** `O(N)`

<hr/>


## Questions

**Ques1 - Explain why you need a max and min heap and what kind of information they store.**

**Solution 1 :**
max_heap stores the smaller half of the numbers in the current window whereas min_heap stores the larger half of the numbers in the current window.

**Ques2 - Explain that Python heap is a min heap and how that affects how you use it**

**Solution 2 :**
Python's heapq module implements a min-heap, meaning the smallest element is always at the root. To simulate a max-heap using Python's min-heap, we store negative values. When inserting a number into the max-heap, we push its negative value. When retrieving the maximum value, we pop the smallest negative value


**Ques3 - Explain why you need balance?**

**Solution 3 :**
Balancing the heaps ensures that the size difference between the two heaps is at most one. This is crucial for efficiently finding the median.


**Ques4 -Explain what the removeindex function does, hint it must maintain the heap condition, but how is that achieved?**

**Solution 4 :**
This function removes a specified element from either heap while maintaining the heap property.We replace the element with the last element in the heap and then remove the last element.If the replaced element is larger than the removed element, perform a _siftup whereas If the replaced element is smaller than the removed element, perform a _siftdown and then balance heaps.