# Data Structures and Algorithms with Python - Video Assignment - 4

**CDA 500**
**Vaibhav Bansal - 50560484**

## Video Link 1 (PATH SUM ||):
https://buffalo.box.com/s/gy1cg9pr7r759quado8jjybftosu5zlp

## PATH SUM ||

**Leetcode Question Link:**

https://leetcode.com/problems/path-sum-ii/

## Code

```python

class TreeNode():
    def __init__(self,val = 0,left = None, right = None):
        self.val = val
        self.left = left
        self.right = right
        
class BinaryTree:

    # Create Binary Tree
    def create_binary_tree(lst,i,n):
        if i < n:
            if lst[i] is None:
                return None
            else:
                root = TreeNode(lst[i])
                root.left = BinaryTree.create_binary_tree(lst, 2 * i + 1, n)
                root.right = BinaryTree.create_binary_tree(lst, 2 * i + 2, n)
                return root
        return None

    # Path Sum Helper Function
    def pathSumUtils(root,target,current_path,matching_path):
        if root is None:
            return
        current_path.append(root.val)
        if root.val == target and root.left is None and root.right is None:
            matching_path.append(list(current_path))
        else:
            if root.left:
                BinaryTree.pathSumUtils(root.left,target-root.val,current_path,matching_path)
            if root.right:
                BinaryTree.pathSumUtils(root.right,target-root.val,current_path,matching_path)
        current_path.pop() #Backtracking

    #Path Sum Function        
    def pathSums(root,target):
        matching_path = []
        BinaryTree.pathSumUtils(root,target,[],matching_path)
        return matching_path

# Binary Tree    
lst=[5,4,8,11,None,13,4,7,2,None,None,None,None,5,1] 

tree_root = BinaryTree.create_binary_tree(lst,0,len(lst))

total_paths = BinaryTree.pathSums(tree_root,22)

print("Total paths",total_paths)
# Total paths [[5, 4, 11, 2], [5, 8, 4, 5]]

```
<hr/>

 - **Time Complexity :** `O(n)`

 - **Space Complexity :** `O(n)`

<hr/>

## Questions

**Ques1 - Explain how each recursion has global information**

**Solution 1**
The recursion has access to global information meant that each recursive call has access to the current_path and matching_path. The `current_path` tracks the current path and is updated as the algorithm traverses the tree whereas
`matching_path` collects all valid paths and is shared across recursive calls.

**Ques2 - Explain why DFS instead of BFS**

**Solution 2**

DFS easily supports backtracking. After reaching the end of a path, it can backtrack to the previous state and explore alternative paths FOR explorING all root-to-leaf paths that sum to a given target value. BFS does not inherently support backtracking in the same way. It processes nodes level by level, so backtracking to explore alternative paths is not as straightforward.

**Ques3 - Explain what backtrace is and why you need it**

**Solution 3**

After exploring a path, current_path.pop() pops off the last node from current_path to backtrack it to the previous state. This allows the function to proceed with other alternative paths from the same parent node so that all possible paths are explored.