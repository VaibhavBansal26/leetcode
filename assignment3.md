# Data Structures and Algorithms with Python - Assignment - 3

**CDA 500**
**Vaibhav Bansal - 50560484**

# Question 1

**Q1 -- Explain in your own words what a linked list is.**

**Answer 1:**

Linked lists are data structures that use nodes to organize information, with each node potentially scattered across different memory locations.This makes the data assignable to any number of memory blocks dynamically and, therefore, it makes its application very flexible. That flexibility may become an advantage for some tasks, in particular those where a large amount of insertions and deletions need to be done continuously. However, linked lists come with an efficiency trade-off, possibly at the cost of more memory and slower access time compared to arrays.

Linked Node -> It has value and reference to the next node.

- Data: The value or data element the node contains (e.g., an integer, string, etc.).
- Next: A reference (or pointer) to the next node in the list.


```python

class LinkedNode:
    def __init__(self, value):
        self.value = value
        self.next = None      

    def __repr__(self):
        return self.value
```

Linked List -> It is a collection of nodes arranged in a linear order.

- Head: A reference to the first node in the list.
- Tail: A reference to the last node in the list (in some implementations). (not mandatory)
- Size: The number of nodes in the list. (not mandatory)

Types:
1. Singly Linked List:

    - Structure: Each node contains data and references to the next node.
    - Usage: Simple to implement and efficient for operations that primarily involve traversing the list in one direction.
    - Example: A list of items to be processed sequentially.

2. Doubly Linked List:

    - Structure: Each node contains data, a reference to the next node, and a reference to the previous node.
    - Usage: More flexible than singly linked lists in such a way that it can traverse in both ways of direction. Useful for applications in which there's a frequent need to be able to add/remove nodes at either end or to traverse backward.
    - Example: Making a web browser's forward and backward navigation.

3. Circular Linked List:

    - Structure: The last node points back to the first node, so we have a circle.
    - Usage: Useful in application programs where the list is to be accessed circularly, for example, in round-robin scheduling.
    - Example: Managing a playlist of songs that should repeat.

4. Circular Doubly Linked List:

    - Structure: Circular list with some features of a doubly linked list. Every node points to both the next and previous node. The list forms a circle.
    - Usage: Useful where one needs the flexibility of a doubly linked list with the circular structure, allowing efficient traversal and modification from any point in the list.
    - Example: The Implementation of Circular Buffer.



# Question 2

**Q2 -- Give the time complexity of the following operations and explain briefly why that is the case.**

1. Insert at beginning
2. Insert at end
3. Delete from beginning
4. Delete from end
5. Search a value
6. Find the index of a value


**Answer 2:**

**1. Insert at beginning**

```python
 def insert_at_beginning(self, value):
        current_head = self.head
        new_node = LinkedNode(value)
        new_node.next = current_head
        self.head = new_node
```
**Time Complexity: -**

`O(1)` -> We just need to create a new node and update its next pointer to the current head, then update the head to this new node.

**2. Insert at end**

```python
 def insert_at_end(self, value):
        if len(self) == 0:
            new_node = LinkedNode(value)
            self.head = new_node
        else:
            current_node = self.head
            while current_node:
                if not current_node.next:
                    current_tail = current_node
                    new_node = LinkedNode(value)
                    current_tail.next = new_node
                    new_node.next = None
                    break
                else:
                    current_node = current_node.next
```

**Time Complexity: -**

`O(n)` -> We just need to traverse the entire list to find the last node, then update its next pointer to the new node.

**3. Delete from beginning**

```python
 def delete_from_beginning(self):
        self.head = self.head.next
```

**Time Complexity: -**

`O(1)` ->  We just need to update the head to the next node in the list.

**4. Delete from end**

```python
 def delete_from_end(self):
        current_node = self.head
        while current_node:
            if current_node.next.next == None:
                current_node.next = None
                break
            else:
                current_node = current_node.next
```

**Time Complexity: -**

`O(n)` -> We just need to traverse the list to find the second-to-last node to update its next pointer to null.

**5. Search a value**

```python
 def search_value(self, value):
        current_node = self.head
        current_node_index = 0 
        while current_node:
            if current_node.value == value:
                return current_node_index
            else:
                current_node = current_node.next
                current_node_index += 1
        return -1
```

Time Complexity: -

`O(n)` -> In the worst case, we may need to traverse the entire list to find the value.

**6. Find the index of a value**

```python
 def find_index(self, value):
        current_node = self.head
        index = 0
        while current_node:
            if current_node.value == value:
                return index
            current_node = current_node.next
            index += 1
        return -1 
```

**Time Complexity: -**

`O(n)` -> Similar to search, we may need to traverse the entire list to find the index of the value.

# Question 3

**Q3 -- On a piece of paper, trace the steps of inserting the value 66 at the third index of the linked list with values [1, 2, 3, 4, 5]. Be creative!**

**Answer 3:**

![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720053504/JPEG_image-4BE3-BADB-1B-0_tobowb.jpg)

# Question 4

**Q4 -- On a piece of paper, trace the steps for reversing the linked list [1, 2, 3, 4, 5]. First, explain all the variables that are initialized and why you need them. Then, step through the algorithm and draw the linked list, and show all the variables at each step. Make sure to point out how the head updates at each step and what happens at the end.**

**Answer 4:**

![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720010180/JPEG_image-4A4B-8FEF-9E-0_h1nof7.jpg)

![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720010179/JPEG_image-4477-A7B9-14-0_t3yjwp.jpg)

# Question 5

**Q5 -- On a piece of paper, trace the steps for detecting a cycle in the linked list [1, 2, 3, 4, 5], where 5 points back to 3. First, explain all the variables that are initialized and why you need them. Then, step through the algorithm and draw the linked list, and show all the variables at each step. Also, Explain what "while slow and fast and fast.next" is doing. Explain what happens when there is no cycle in a linked list. Explain how fast and slow traversing detects a cycle.**

**Answer 5:**

**Variables Initialization**

 - slow: This pointer moves one step at a time.
 - fast: This pointer moves two steps at a time.
 - head: The starting node of the list.

These pointers help in determining if a cycle exists by comparing their positions as they traverse the list.

Initial State

List: 1 -> 2 -> 3 -> 4 -> 5 -> 3 (cycle)

 - slow: head (initially points to node 1)
 - fast: head (initially points to node 1)
 - Explanation of while slow and fast and fast.next

The condition while slow and fast and fast.next ensures that the traversal continues as long as:
 
 - slow is not None.
 - fast is not None.
 - fast.next is not None.

If any of these conditions fail, it means we've reached the end of a non-cyclic list, and there is no cycle.

**Explanation**

**1. while slow and fast and fast.next:** This loop continues as long as slow, fast, and fast.next are not None. If either fast or fast.next becomes None, it means there is no cycle (since fast can reach the end of the list).

**2. No cycle:** If the loop exits because fast or fast.next becomes None, there is no cycle in the list.

**3. Cycle detection:** When slow and fast meet, it means that fast has caught up to slow within the cycle, confirming the presence of a cycle.

![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720012227/JPEG_image-4616-A1DA-79-0_dys3gd.jpg)


# Question 6

**Q6 -- On a piece of paper, trace the steps for deleting a value from a linked list. The linked list is [1, 2, 3, 4, 5], and delete the value 3. First, explain all the variables that are initialized and why you need them. Then, step through the algorithm and draw the linked list, and show all the variables at each step.**


**Answer 6:**

Variables Initialization

 - current_node: This pointer is used to traverse the linked list. It starts at the head of the list.
 - previous_node: This pointer keeps track of the node before current_node. It starts as None because there is no previous node for the head.

Algorithm for Deleting a Value

 - Traverse the list using current_node.
 - If current_node.value matches the value to be deleted (3 in this case):
 - If previous_node is None, it means we are deleting the head node. Update self.head to current_node.next.
Otherwise, set previous_node.next to current_node.next to remove current_node from the list.
 - If no match is found and the end of the list is reached, return -1.

```python
def delete_value(self, value):
    current_node = self.head
    previous_node = None
    while current_node:
        if current_node.value == value:
            if previous_node is None:
                self.head = self.head.next
            else:
                previous_node.next = current_node.next
            return current_node.value
        else:
            previous_node = current_node
            current_node = current_node.next
    return -1

```

![Description](https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720013558/JPEG_image-4056-82E0-B4-0_zsvw62.jpg)


<hr/>