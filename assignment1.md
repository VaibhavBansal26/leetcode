# Data Structures and Algorithms with Python - Assignment - 1

**CDA 500**
**Vaibhav Bansal - 50560484**

## Q1. What is a Data Structure?

**Answer 1:**

Data structures refer to how data is organized. It not only organize our data but also influence the efficiency of our code. Each data structure is designed to organize data to suit specific purposes so that various operations can be performed efficiently. 

## Q2. The first data structure we studied is a list, and we summarized seven properties of a list by asking seven questions. Answer these seven questions for a list and what the answer means. These answers should be about Python lists, not any other language. Use average case

**Answer 2:**

Python lists are versatile data structures that allow dynamic resizing and can hold mixed data types. Here are seven important properties characterized by specific questions:

#### 1. Reading/Indexing (1 step)
- **Answer**: It takes 1 step.Retrieving an element from a Python list using its index is a constant time operation, represented as \(O(1)\). Python lists are implemented as dynamic arrays, allowing for direct access to any element using its index.

#### 2. Searching for a Value Not Contained Within the List (100 steps)
- **Answer**: 100 steps on average.If the value is not in the list, Python must examine each item until the end is reached. This results in a linear search time complexity of \(O(n)\), where \(n\) is the number of items in the list.

#### 3. Insertion at the Beginning of the List (101 steps)
- **Answer**: It costs 101 steps on average.Inserting an element at the beginning of a Python list involves shifting all existing elements to the right to make room. This operation is \(O(n)\) as it requires moving all elements in the list.

#### 4. Insertion at the End of the List (1 step Amortized)
- **Answer**: It takes 1 step, on average, in an amortized way.Appending an item at the end of the list typically has a time complexity of \(O(1)\). Occasionally, if the underlying array is full, Python must allocate a larger array and copy all elements, but this cost is amortized over many append operations.

#### 5. Deletion at the Beginning of the List (100 steps)
- **Answer**: In amortized terms, costs 100 steps.Deleting the first element requires shifting all other elements one position to the left. This is also an \(O(n)\) operation.

#### 6. Deletion at the End of the List (1 step)
- **Answer**: It costs 1 step.Deleting the last element is an \(O(1)\) operation, as no shifting of elements is required, making it efficient in terms of time complexity.

#### 7. Sorting the List (O(n log n))
- **Answer**: Sorting a list has a time complexity of \(O(n log n)\).Sorting typically uses algorithms like Timsort, a hybrid based on merge sort and insertion sort, which achieves \(O(n log n)\) complexity. This efficiency makes it suitable for sorting large datasets as the complexity increases logarithmically with list size.


## Q3. Why do you need to study different data structures? Why is a list not sufficient? Hint: Answer these questions by discussing operations you can perform on data structures.

**Answer 3:**

It is essential to study different data structures because each data structure has specific benefits and efficiencies in the operations of searching, inserting, deleting, sorting, and appending. The selection of a data structure significantly influences the time efficiency of an algorithm. Even though a list (or array) is a primary data structure, sometimes it cannot perform operations in the most effective way within the context.

Other data structures that can be considered:

#### 1. Searching
- **List**: An unsorted list will take \(O(n)\) time because each element must be inspected. For a sorted list, the best time for searching is \(O(log n)\), achievable through binary search.
- **Hash Table (unsorted)**: Provides an average search time of \(O(1)\), which is significantly better than a list.
- **Binary Search Tree (BST)**: Allows an \(O(log n)\) search time if the tree is balanced.

#### 2. Insertion at the Beginning
- **List**: In the case of a dynamic array, this operation takes \(O(n)\) because all elements need to be shifted.
- **Linked List**: This operation can be performed in \(O(1)\).

#### 3. Insertion at the End
- **List**: If within its capacity, it is done in \(O(1)\). If resizing is needed, then it is \(O(n)\).
- **Linked List**: Also \(O(1)\) if we maintain a tail pointer; otherwise, it's \(O(n)\).

#### 4. Deletion from the Beginning
- **List**: Requires \(O(n)\) time because it involves shifting all elements.
- **Linked List**: Can be done in \(O(1)\) by adjusting the head pointer.

#### 5. Deletion from the End
- **List**: Typically \(O(1)\) unless it triggers a resize of the underlying array.
- **Linked List**: Requires \(O(n)\) to find the last but one element unless a tail pointer and a reference to the penultimate node are maintained.

#### 6. Sorting
- **List**: Sorting an array can be efficient, with algorithms like QuickSort and MergeSort offering an average complexity of \(O(n log n)\). However, these operations are complex to implement correctly.
- **Linked List**: Sorting is generally slower and more complex due to pointer handling overhead, though merge sort can be adapted to run in \(O(n log n)\).

#### 7. Appending
- **List**: Appending is \(O(1)\) when space is available; resizing incurs an average time complexity of \(O(1)\) due to the amortized cost of copying.
- **Linked List**: Generally \(O(1)\) with a tail pointer; resizing is not needed.

Although lists are simple and useful for many applications, their limitations in specific operations can lead to inefficient programs, particularly with large data sets or frequently performed operations. By understanding and utilizing different data structures, such as linked lists, hash tables, trees, and graphs, we can optimize our algorithms to be more efficient and system-friendly based on the specific needs of the operation. 


## Q4. What is an Algorithm?

**Answer 4:**

An algorithm is simply a set of instructions for completing a specific task. It is a series of instructions that are executed to perform a specific task or to compute a result.

## Q5. Time complexity of algorithms is measured in terms of steps instead of pure time. Why is that?

**Answer 5:**

Hardware-independent performance measurement is why steps are used to measure time complexity. It quantifies the algorithm based on N, where N is the number of elements in a list. Measuring in time units, such as seconds, would vary with processor speed and other system-specific factors, so making comparisons between algorithms becomes a bit difficult.

## Q6. We compared linear search to binary search. Which searching algorithm is better and why? Answer this answer by first talking about what binary search assumes and the cost of ensuring that assumption. Then compare how many steps it would take linear search to find an element vs binary search.

**Answer 6:**

The costs of a binary search depend heavily on a key precondition: the array must be sorted. This is crucial because binary search operates by continually halving the search interval. If the array is unsorted, binary search could overlook the target value, leading to incorrect results. The primary cost involved in maintaining this precondition is the effort required to sort the array, which typically incurs a time complexity of \(O(n log n)\) using standard sorting algorithms like mergesort or quicksort.

**Comparing how many steps it would take linear search to find an element vs binary search**

- **100-element array:**
  - Linear Search: 100 steps
  - Binary Search: 7 steps

- **10,000-element array:**
  - Linear Search: 10,000 steps
  - Binary Search: 13 steps

- **1,000,000-element array:**
  - Linear Search: 1,000,000 steps
  - Binary Search: 20 steps

- **200-element array:**
  - Linear Search: 200 steps
  - Binary Search: Steps are not precisely defined as either 8 or 14 but should theoretically be closer to 8 (since \(\log_2(200) \approx 7.64\)).

**Linear Search** scans each element of the array sequentially, starting from the first element and continuing until the target element is found or the end of the array is reached. Its performance is \(O(n)\), where \(n\) is the number of elements in the array. Linear search does not require the array to be sorted and is straightforward to implement, but its time to complete increases significantly as the size of the array grows.

**Binary Search** exhibits a time complexity of \(O(log n)\), making it increasingly efficient for handling large datasets. The graph and data show that the number of steps required for binary search grows very slowly compared to linear search. This efficiency makes binary search particularly advantageous for large datasets, assuming the array is already sorted or can be sorted without incurring excessive costs.

