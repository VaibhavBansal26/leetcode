# Data Structures and Algorithms with Python - Video Assignment - 1

**CDA 500**
**Vaibhav Bansal - 50560484**

## Max Product Code Video Link:
https://buffalo.app.box.com/s/f5b6tuxc0wky95d94ca21n0nbbojjfop

## Find Duplicates Code Video Link:
https://buffalo.app.box.com/s/ukvuaviclx33hk9jll82y9f1koe2g4gr

# Question 1: Max Product

https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array

## Solution 1

**Ques:How does the first solution with two loops tackle the problem? What is it is time and space complexity and how do you know this?**

**Code :**

```python
from typing import List
nums = [-100,-99,3,4]
def maxProduct(nums: List[int]) -> int:
    length = len(nums)
    max_prod = 0
    max_indices = (0, 0)
    for i in range(length):
        current_val = nums[i]
        j = i + 1
        while j < length:          
            next_val = nums[j]
            prod = current_val * next_val
            if prod > max_prod:
                max_vals = (nums[i], nums[j])
                max_prod = prod
            j += 1
    i, j = max_vals      
    max_prod = (i-1) * (j-1)    
    return max_prod
            
maxProduct(nums)   
```

**Time Complexity:** `O(n^2)` 

- Nested loop is present in the code

**Space Complexity:** `O(1)` 

- The space complexity is 𝑂(1) because the additional space used does not grow with the size of the input list

**Explanation:** - The time complexity of this approach is O(n^2) because it involves nested loops to compare each element with every other element.The space complexity is 𝑂(1) because the additional space used does not grow with the size of the input list. It initializes the variables that will store the maximum product found (max_prod) and the indices that formed it (max_indices). The function then uses a nested loop to scan over all possible pairs of elements in the list: the outer loop scans over each component and the other scans over the successive elements to form pairs. It computes the product for each pair and updates max_prod and max_vals if the current product is higher than what it records. Then, having the best pair in the end, the values are updated through - 1 from each, and then the last product is re-computed.


# Solution 2

**Ques:How does the second solution using sorting work? What is the time and space complexity and how do you know this?**

**Code :**

```python
nums = [1,5,4,5]
def maxProduct(nums: List[int]) -> int:
    nums.sort() # n log n
    length = len(nums)
    return (nums[length-1]-1) * (nums[length-2]-1)
maxProduct(nums)  
```

**Time Complexity:** `O(nlogn)`

- O(nlogn) due to the sorting step

**Space Complexity:** `O(1)`

- The space complexity is O(1) for the additional variables used (length and the return value), since the sorting is done in place and no extra data structures are used.

**Explanation:** O(nlogn) due to the sorting step.O(1) for the list itself, but up to O(n) due to auxiliary space used by the sorting algorithm.Once sorted, the two largest elements in the list will be the last two elements. The function then calculates the product of these two largest elements, each decremented by 1, by accessing them through their index and return their product. 

# Solution 3

**Ques:How does the third solution work? How can you modify it to handle the case for two large negative numbers?  What is the time and space complexity and how do you know this? What is the main trick or insight that you learned from the final solution? HINT: How are you storing two max or two min values in just one loop.**

**Code :**

```python
nums = [-100,-99,3,4]
def maxProduct(nums: List[int]) -> int:
    max_val = float('-inf')
    max_val_1 = float('-inf')
    min_val = float('inf')
    min_val_1 = float('inf')
    for val in nums:
        if val > max_val:
            max_val_1 = max_val
            max_val = val
        elif val > max_val_1:
            max_val_1 = val
            
        if val < min_val:
            min_val_1 = min_val
            min_val = val
        elif val < min_val_1:
            min_val_1 = val
        
    max_res = (max_val-1) * (max_val_1-1)
    min_res = (min_val-1) * (min_val_1-1)

    return max(max_res, min_res)
    
maxProduct(nums)  
```

**Time Complexity:**`O(n)` 

- The code iterates through the list exactly once, performing constant-time operations within the loop.

**Space Complexity:** `O(1)`

- The space complexity of the given code is O(1), which means it uses a constant amount of extra space regardless of the input size.

**Explanation:**
finding the maximum product of two distinct elements in a list nums, after decrementing each by 1. It initializes four variables to track the two largest (max_val, max_val_1) and two smallest (min_val, min_val_1) values. As it iterates through the list, it updates these variables accordingly. After the loop, it computes the products of the two largest and the two smallest values, each decremented by 1. Finally, it returns the larger of these two products. This approach ensures that the function accounts for both large positive values and large negative values that could result in a high positive product.

# Question 2: Find Duplicates

https://leetcode.com/problems/find-all-duplicates-in-an-array/

## Solution 1

**Ques: How does the first solution using set and dictionary work? What is it is time and space complexity and how do you know this? Also, does it meet the criteria set by the problem?**

**Code :**

**Using Dictionary**

```python
lst = [1, 3, 1, 3, 5, 1, 4, 7, 7]
def find_duplicates(lst):
    result = []
    seen = {}
    
    for val in lst:
        if val not in seen:
            seen[val] = 1
        else:
            result.append(val)
            
    return result
find_duplicates(lst)
```

**Using Sets**

```python
lst = [1, 3, 1, 3, 5, 1, 4, 7, 7]
def find_duplicates(lst):
    result = []
    seen = set()
    
    for val in lst:
        if val not in seen:
            seen.add(val)
        else:
            result.append(val)
            
    return result
find_duplicates(lst)
```

**Time Complexity:** `O(n)` 

- Iterating through the list to count occurrences takes O(n) time, where n is the number of elements in the list.

**Space Complexity:** `O(n)`

- The dictionary counter stores a count for each unique element in the list. In the worst case, if all elements are unique, the dictionary will have n entries.

**Explanation**

The first function find_duplicates uses a dictionary to track seen elements and identify duplicates in the list lst. As it iterates through the list, it checks if each element is already in the dictionary. If not, the element is added to the dictionary; if it is, the element is appended to the result list as a duplicate. The second function find_duplicates uses a set for the same purpose. It iterates through the list, checking if each element is in the set. If not, the element is added to the set; if it is, the element is appended to the result list as a duplicate

**Does It Meet the Criteria?**

The problem criteria often include constraints on time and space complexity. While this solution efficiently finds duplicates in linear time, it does not meet the space complexity requirement of O(1) extra space as specified by certain problem constraints (such as the LeetCode problem that requires O(n) time and O(1) extra space).

 - Time Complexity: O(n) - This is efficient and meets the criteria for linear time complexity.

 - Space Complexity: O(n) - This does not meet the O(1) extra space requirement because it uses a dictionary to store counts.

# Solution 2

**Ques: How does the second solution work using a list to mark things as seen?  What is it is time and space complexity and how do you know this?**

**Code :**

```python
lst = [4,3,2,5,2,3]
def find_duplicates(lst):
    result = []
    for ele in lst:
        if lst[abs(ele) - 1] < 0:
            result.append(abs(ele))
        else:        
            lst[abs(ele)-1] *= -1
            print(ele, lst)
            
    return result
find_duplicates(lst)
```

**Time Complexity:** `O(n)` 

- The algorithm iterates through the list once, performing constant-time operations for each element. The loop runs n times.

**Space Complexity:** `O(1)`

- The algorithm modifies the input list lst in place, which does not require additional space beyond the input list itself.

**Explanation:**

The second solution modifies the input list by marking elements seen, implemented by changing the sign of the value at their specific index. This in-place modification uses no extra space, only requiring the output list. The algorithm goes through the list, element by element, and uses the absolute value of each element to access a corresponding index. If the value of the new index is negative, it implies that the number has been encountered before and thus is repeated. Now, if the value at this index is positive, it is clear that the element has not been seen before; hence, we mark it as seen by changing the value at that index to the negative value of its current positive value.


## Visual Representation

**Ques: how the list solution works by stepping through array one step at a time. You can also put your drawing or visual aids on paper and scan it or take a picture of it.**

# List solution works by stepping through array one step at a time.

![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720127142/JPEG_image-476C-9AC2-31-0_wdm2dp.jpg)
![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720127142/JPEG_image-46BA-8610-86-0_smoafb.jpg)
![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720127141/JPEG_image-41A4-92C6-22-0_wobxqe.jpg)