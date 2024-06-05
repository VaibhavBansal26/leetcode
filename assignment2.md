# Python Time Complexity Patterns 


# Question 1

## Time Complexity: `O(1)`
- Operations do not depend on the size of the input data.

## Space Complexity: `O(1)`
- No additional space is used that scales with input size.

```python
# Constant Time Function
def constant_time_func(lst):
    return lst[1]

def constant_time():
    x = 1
    x += 1
    print("Constant Time Output:", x)
```
Explanation :The constant_time_func and constant_time perform operations that do not depend on input size.

# Question 2 

## Time Complexity: `O(N)`
perations scale linearly with the input size.

## Space Complexity: `O(1)`
Uses a constant amount of additional space regardless of input size.

```python
def loop(N):
    count = 0
    for _ in range(N):
        count += 1
    return count

def func(lst):
    lst.insert(0, 10)


```
Explanation : linear_time_loop counts up to N, performing N operations. linear_time_insert performs a single operation that takes linear time relative to the list size.

# Question 3 

## Time Complexity: `O(N^2)`
Nested loops each run up to N times.

## Space Complexity: `O(1)`
No additional space that scales with the square of the input size is used.

```python
def nested_loop(N):
    count = 0
    for _ in range(N):
        for _ in range(N):
            count += 1
    return count

def nested_loop(lst):
    count = 0
    N = len(lst)
    for ele in range(N):
        lst.insert(0, ele)


```
Explanation: quadratic_time_nested_loop runs two nested loops each up to N, resulting in N^2 operations. quadratic_time_insert performs increasingly costly insert operations as the list grows.

# Question 4 

## Time Complexity: `O(N/K)`
Iterates over N elements with steps of size k.

## Space Complexity: `O(1)`
Uses a constant amount of space.

```python
def loop(N, k):
    for _ in range(N, 1, -k):
        pass

```
Explanation: loop_with_step iterates with steps decrementing by k, affecting loop count.


# Question 5

## Time Complexity: `O(N^2/K)`
Scaled quadratic time complexity due to varying loop steps.

## Space Complexity: `O(1)`
Constant space usage, regardless of the nested iteration structure.

```python
def func(N):
    for _ in range(N, 1, -3):
        for _ in range(N, 1, -2):
            pass


```
Explanation : nested_loops_diff_steps shows nested loops with different decrement rates.

# Question 6 

## Time Complexity: `O(logN)`
Number of operations decreases logarithmically with each iteration.

## Space Complexity: O(1)
Uses a fixed amount of space regardless of the size of N.

```python

def func(N):
    i = 1
    count = 0
    while (i < N):
        i *= 2
        count += 1
    return count

```
Explanation : doubles a counter, reducing the needed steps logarithmically with respect to N.
