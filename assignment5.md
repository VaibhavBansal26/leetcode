# Data Structures and Algorithms with Python - Video Assignment - 2

**CDA 500**
**Vaibhav Bansal - 50560484**

## Video Link 1 (Two Pointer, 2SUM, 3SUM):
https://buffalo.box.com/s/b8rmkytrbl91akxl7ujxnr2p4wdploa8

## Video Link 2 (Water Container Problem):
https://buffalo.box.com/s/xkp6329i65761a1s7ryz2a6x1ku91foe

## Questions (Video 1)

**Ques 1 -- Explain the two-pointer pattern and illustrate how it works for checking if a string is a palindrome. Use examples like MADAM, ()(), and )()(. You must visually show the two pointers moving using PowerPoint, OneNote, or any other software. You can also use paper to draw the illustration and scan or take a picture of it.**

**Solution 1**

In this pattern, you initialize two pointers (indices) and iterate over an array until a certain condition is satisfied. Essentially, using two pointers allows you to keep track of two values simultaneously. Therefore, whenever you need to maintain information about two values, this pattern should be employed. The two pointers can be utilized to iterate in either one or two directions.

Two pointers is an extremely common technique used to solve array and string problems. It involves having two integer variables that both move along an iterable. This means we will have two integers, usually named something like i and j, or left and right which each represent an index of the array or string.

**Valid Palindrome**

```python
def valid_palindrome(string):
    left_index = 0
    right_index = len(string)-1
      
    while left_index < right_index:
        if string[left_index] != string[right_index]:
            return False
        
        left_index += 1
        right_index -= 1
        
    return True

  
valid_palindrome('MADAM')
```

## Visual Presentation

<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720455565/JPEG_image-48E7-8964-21-0_newo0m.jpg" width="70%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720455565/JPEG_image-4EFD-8006-05-0_x798nj.jpg" width="70%" />

**Ques 2 -- discuss the 2sum problem and explain how the two-pointer solution works. First, visually solve the following example:**

  - **Input: nums = [2, 7, 11, 15], target = 9**

  - **Output: [0, 1]**

  - **Explanation: Because nums[0] + nums[1] equals 9, we return [0, 1]**

**Solution 2**

```python
    def two_sum(nums, target):
        left, right = 0, len(nums) - 1
        while left < right:
            current_sum = nums[left] + nums[right]
            if current_sum == target:
                return [left, right]
            elif current_sum < target:
                left += 1
            else:
                right -= 1
        return []

    # Example usage:
    nums = [2, 7, 11, 15]
    target = 9
    print(two_sum(nums, target))  # Output: [0, 1]
```

- **Time Complexity: O(n)**
Since the pointers move inward from the start and end of the list and converge towards each other, the loop runs at most n/2 iterations, where n is the length of the list. Therefore, the overall time complexity of the function is O(n).

- **Space Complexity: O(1)**
The function uses the input list nums, but since it doesn't modify or duplicate it, this is not considered extra space.The function uses a constant amount of extra space for the pointers left and right, as well as the temporary variable current_sum.

**Insight**

The 2sum problem involves finding two numbers in a sorted array that add up to a specific target. The main trick or insight here is to use two pointers starting at the beginning and end of the array and move them based on the sum of the pointed values.



## Visual Presentation

<img src ="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418111/JPEG_image-4925-92CE-2E-0_sbfv3g.jpg" width = "70%" />



**Ques 3 -- introduce the 3sum problem and explain how it differs from the 2sum problem. Also, discuss how the two-pointer solution can be utilized to solve the 3sum problem. Focus on comparing 2sum and 3sum, highlighting the differences and the adjustments needed to solve the 3sum problem. Include the code and a brief explanation in the HTML file**

**Solution 3**

```python
def threeSum(nums, target):
    nums.sort()
    t=set()
    for i in range(len(nums) - 2):
        l,j=i+1,len(nums)-1
        while l < j:
            total = nums[i] + nums[l] + nums[j]
            if total > 0:
                j-=1
            elif total < 0:
                l+=1
            elif total == 0:
                t.add((nums[i],nums[l],nums[j]))
                l += 1
                j -= 1
    return list(t)

nums = [-1, 0, 1, 2, -1, -4]
target = 0
print(threeSum(nums, target))  # Expected output: [(-1, -1, 2), (-1, 0, 1)]
```

 - **Time Complexity: O(N^2)**

 - **Space Complexity: O(N) in the worst case, due to the storage of triplets in combinations.**

**Insight**

The main trick is leveraging the sorted nature of the array to efficiently adjust the pointers to find valid triplets without redundant checks, thus reducing the problem complexity compared to a naive three-loop approach, which would lead to a N^3 solution.

The 3sum problem is an extension of the 2sum problem where you need to find three numbers in an array that add up to zero. The main insight is to fix one number and then use the two-pointer technique to find the other two numbers.

#### Comparison with 2sum
- **2sum:** Find two numbers that sum to a target.
- **3sum:** Find three numbers that sum to zero by fixing one number and using 2sum for the remaining array.

## Visual Presentation

<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418110/JPEG_image-4919-BFF3-D9-0_gecxml.jpg" width="70%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418110/JPEG_image-4BC2-B838-3C-0_zvb8ny.jpg" width="70%"/>


## Questions (Video 2)

**Ques 4 --  introduce the water container problem. Visually demonstrate how it works. Explain the logic used to determine the direction in which the pointer moves and how it differs from 2sum and 3sum. Provide reasons for these differences.**

**Solution 4**

**Brute Force**

```python
def maxArea(height):
    max_area = 0
    for left_index in range(len(height)):
        for right_index in range(left_index + 1, len(height)):
            width = right_index - left_index
            low_height = min(height[left_index], height[right_index])

            area = width * low_height

            if area > max_area:
                max_area = area
    return max_area

height = [1,8,6,2,5,4,8,3,7]
maxArea(height)
```

 - **Time complexity: O(N^2)**

 - **Space complexity: O(1)**

**Optimized Code**

```python
def maxArea(height):
    height = [1,8,6,2,5,4,8,3,7]
    max_area = 0

    left_index = 0
    right_index = len(height)-1

    while left_index < right_index:
        width = right_index - left_index
        low_height = min(height[left_index], height[right_index])
        area = width * low_height
        if area > max_area:
            max_area = area
        if height[left_index] <= height[right_index]:
            left_index += 1
        else:
            right_index -= 1
    return max_area

height = [1,8,6,2,5,4,8,3,7]
maxArea(height)
```

 - **Time complexity: O(N)**

 - **Space complexity: O(1)**

**Insight**

The key insight of the two-pointer technique is to maximize the area by starting with the widest possible container and then narrowing the width while trying to increase the height. We always move the pointer that points to the shorter height because the area is determined by the shorter of the two heights. By moving the pointer at the shorter height, we have a chance of finding a taller height that might increase the area.

## Visual Presentation

<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418110/JPEG_image-49C5-9B20-1C-0_e4wtnd.jpg" width="60%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418110/JPEG_image-4088-8528-4B-0_nbkj3l.jpg" width="60%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418110/JPEG_image-497B-A637-16-0_tocsq6.jpg" width="60%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418112/JPEG_image-49BB-9796-94-0_qlzmtf.jpg" width="60%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720418109/JPEG_image-4459-8F27-42-0_mhtps5.jpg" width="60%"/>



**Explain the logic used to determine the direction in which the pointer moves and how it differs from 2sum and 3sum**

**Explanation :**

**Differences from 2sum and 3sum**
2sum and 3sum: Focus on finding specific elements that sum to a target value. Pointers move based on the sum of the values at the pointers.
Water Container: Focus on finding the maximum area. Pointers move based on the height of the lines to maximize the potential area.

The key difference is in the criteria for moving the pointers. In 2sum and 3sum, the pointers move based on the comparison between the sum of the elements and the target value. In the Water Container problem, the pointers move based on the comparison between the heights of the lines.

