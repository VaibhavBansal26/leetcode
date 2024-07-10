# Data Structures and Algorithms with Python - Video Assignment - 3

**CDA 500**
**Vaibhav Bansal - 50560484**

## Video Link 1 (STACK):
https://buffalo.box.com/s/gy1cg9pr7r759quado8jjybftosu5zlp

## Questions

**Ques 1  Explain what a Stack is, covering its basic functionalities such as push, pop, and read/peek. Discuss the time complexities associated with implementing a stack using a list versus a linked list. Explain the reasons behind the differences in time complexities.**

**Solution 1**

A Stack is a linear data structure that follows the Last In, First Out (LIFO) principle. This means that the last element added to the stack will be the first one to be removed.Stacks and queues are not new a data structure. Rather, they are simply arrays with restrictions. It is is these restrictions that makes them so elegant. They are elegant tools for handling temporary data. Temporary data is information that does not have any meaning after it is processed, so you can throw it away once you are done with it. Stacks and queues handle temporary data, but they have a special focus on the order in which the data is handled.

A stack stores data in the same way arrays do, except that they have three restrictions.

- Data can be inserted only at the end of a stack
- Data can be deleted only from the end of a stack
- Only the last element of a stack can be read

The beginning of the stack is its bottom and the end of the stack is its top. Stacks are LIFO -- last in first out! A stack class is simply an interface that forces the users to interact the array in a limited ways. A stack class only allows reading the last element, appending to the list, and removing the last element from the list. A stack DOES NOT have to be built using a list, you can also use a linked list. Stack is considered an abstract data type because it is built on top of other built-it data structures.

**Basic Functionalities of a Stack**

- **Push:** Add an element to the top of the stack.
- **Pop:** Remove and return the top element from the stack.
- **Read/Peek:** Return the top element without removing it from the stack.

## Using List

```python
class StackList:
    def __init__(self):
        self.stack = []

    def push(self, item):
        self.stack.append(item)

    def pop(self):
        if not self.is_empty():
            return self.stack.pop()
        else:
            return "Stack is empty"

    def peek(self):
        if not self.is_empty():
            return self.stack[-1]
        else:
            return "Stack is empty"

    def is_empty(self):
        return len(self.stack) == 0

# Example usage
stack = StackList()
stack.push(1)
stack.push(2)
print(stack.peek())  # Output: 2
print(stack.pop())   # Output: 2
print(stack.pop())   # Output: 1
print(stack.pop())   # Output: Stack is empty

```

**Time Complexities:**

- **Push:** O(1) - Appending an element to the end of a list is an O(1) operation in most list implementations.
- **Pop:** O(1) - Removing the last element of the list is also O(1) as it involves simply shortening the list.
- **Peek:** O(1) - Accessing the last element of the list is an O(1) operation.

## Using Linked List

```python

class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

class StackLinkedList:
    def __init__(self):
        self.top = None

    def push(self, item):
        new_node = Node(item)
        new_node.next = self.top
        self.top = new_node

    def pop(self):
        if not self.is_empty():
            popped_value = self.top.value
            self.top = self.top.next
            return popped_value
        else:
            return "Stack is empty"

    def peek(self):
        if not self.is_empty():
            return self.top.value
        else:
            return "Stack is empty"

    def is_empty(self):
        return self.top is None

# Example usage
stack = StackLinkedList()
stack.push(1)
stack.push(2)
print(stack.peek())  # Output: 2
print(stack.pop())   # Output: 2
print(stack.pop())   # Output: 1
print(stack.pop())   # Output: Stack is empty

```
**Time Complexities:**

- **Push:** O(1) - Adding an element to the top of the stack (head of the linked list) is O(1) because it involves updating a few pointers.
- **Pop:** O(1) - Removing the top element (head of the linked list) is O(1) as it requires reassigning the head pointer
- **Peek:** O(1) - Accessing the top element of the stack (head of the linked list) is O(1).

Using a linked list, these operations are also constant time because we are only manipulating pointers and not traversing the list.

**Comparing Time Complexities**

Both list-based and linked list-based implementations of a stack provide O(1) time complexity for push, pop, and peek operations. The reason behind this is that both implementations involve only adding or removing elements from the top of the stack, which can be done in constant time.

However, there are some subtle differences in terms of space complexity and potential performance considerations:

**Space Complexity:**

 - **List:** The list-based stack may allocate more memory than necessary because lists in Python are dynamic arrays and may over-allocate to avoid frequent resizing.

 - **Linked List:** The linked list-based stack uses exactly as much memory as needed for the elements plus a small overhead for the pointers.

**Performance Considerations:**

 - **List:** Appending and popping from the end of the list is usually very fast due to contiguous memory allocation. However, if the list needs to resize (i.e., allocate a new, larger array and copy elements), it can occasionally incur a higher cost.

 - **Linked List:** Operations are guaranteed to be O(1) because there is no resizing, but the overhead of managing the pointers and potentially higher memory usage for small elements can make it slightly less efficient in terms of raw performance.

In conclusion, while both implementations offer O(1) time complexity for the primary stack operations, the choice between using a list and a linked list may depend on specific use cases, memory considerations, and language-specific performance characteristics.



**Ques 2 Use visual aids to demonstrate how a stack can be utilized as a linter and provide an explanation of the code that achieves the linting functionality. Present three scenarios:**

   - **a. No mismatch**

   - **b. Missing closing brace, which could be any of the following: ]}),]}**

   - **c. Missing opening brace, which could be any of the following: ([{**

**Solution 2**

A stack can be used effectively to check for balanced parentheses (including curly braces and square brackets) in a string. This is a common linting task, often used in programming languages to ensure that all opening brackets have corresponding closing brackets in the correct order.

**Linting Scenarios**

- **No Mismatch:** The string has perfectly matched parentheses.
- **Missing Closing Brace:** The string has one or more opening braces without corresponding closing braces.
- **Missing Opening Brace:** The string has one or more closing braces without corresponding opening braces.

```python
def lint_parentheses(input_string):
    stack = []
    opening_braces = "({["
    closing_braces = ")}]"
    matches = {')': '(', '}': '{', ']': '['}

    for char in input_string:
        if char in opening_braces:
            stack.append(char)
        elif char in closing_braces:
            if stack and stack[-1] == matches[char]:
                stack.pop()
            else:
                return f"Error: Unmatched closing brace '{char}'"
    
    if stack:
        return f"Error: Unmatched opening brace '{stack[-1]}'"
    
    return "No mismatch"

# Example strings for demonstration
example_1 = "{[()]}"       # No mismatch
example_2 = "{[()]"        # Missing closing brace
example_3 = "{[())]}"      # Missing opening brace

# Results
print(lint_parentheses(example_1))  # No mismatch
print(lint_parentheses(example_2))  # Error: Unmatched opening brace '{'
print(lint_parentheses(example_3))  # Error: Unmatched closing brace ')'

```

## Visual Representation

<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720488484/JPEG_image-4273-AA55-80-0_u3huwd.jpg" width="60%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720488484/JPEG_image-424B-BDC1-95-0_pyzttu.jpg" width="60%"/>
<img src="https://res.cloudinary.com/vaibhav-codexpress/image/upload/v1720488484/JPEG_image-47B9-B76C-EC-0_ahannw.jpg" width="60%"/>



