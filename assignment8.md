# Data Structures and Algorithms with Python - Video Assignment - 5

**CDA 500**
**Vaibhav Bansal - 50560484**

## Video Link 1 (Find Largest Value in Each Tree Row): -->

https://buffalo.box.com/s/9ozl37o0bryq1w3ikayi7vv62nkx93yo

## Find Largest Value in Each Tree Row

**Leetcode Question Link:**

https://leetcode.com/problems/find-largest-value-in-each-tree-row/

## Code

## Iterative method

```python

def largestValues(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return
        results = []
        q = []
        q.append(root)
        while q:
            currentLength = len(q)
            currentLevelMax = float(-inf)
            for _ in range(currentLength):
                n = q.pop(0)
                currentLevelMax = max(currentLevelMax, n.val)
                if n.left:
                    q.append(n.left)
                if n.right:
                    q.append(n.right)
            results.append(currentLevelMax)
        return results

Input: root = [1,3,2,5,3,null,9]
Output: [1,3,9]
```
<hr/>

 - **Time Complexity :** `O(N)`

 - **Space Complexity :** `O(N)`

<hr/>

## Recursion

```python
def largestValues(self, root: Optional[TreeNode]) -> List[int]:
        levels = []
        def helper(root,level):
            if root is None:
                return levels
                
            if len(levels) == level:
                levels.append([])

            levels[level].append(root.val)

            if root.left:
                helper(root.left,level+1)
            if root.right:
                helper(root.right,level+1)
            
        helper(root,0)
        return [max(i) for i in levels]

Input: root = [1,3,2,5,3,null,9]
Output: [1,3,9]

```

<hr/>

 - **Time Complexity :** `O(N)`

 - **Space Complexity :** `O(H)`

<hr/>


## Questions

**Ques1 - Explain why you need a queue and how it is used**

**Solution 1 :**
Queue data structure is needed to store and track nodes level by level. Queue follows First In First Out (FIFO) approach which naturally aligns with the level order traversal approach.

**Ques2 - Explain why BFS instead of DFS**

**Solution 2 :**
As the question has asked about the maxinmum value at each level, In that case, BFS is more suitable than DFS as BFS tranverse nodes level by level whereas DFS dives deep into the tree before backtracking, which is not naturally aligned to track the max values at each level.

**Ques3 - How is the max found for each level?**

**Solution 3 :**
At each level of BFS, we can iterate over all the nodes at that particular level to find the maximum value at that particular level.