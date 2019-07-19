# LeetCode - Leaf-Similar Trees
[Leaf-Similar Trees - LeetCode](https://leetcode.com/problems/leaf-similar-trees/)

## Solution
```
class Solution {
    func leafSimilar(_ root1: TreeNode?, _ root2: TreeNode?) -> Bool {
        return getLeaf(root1) == getLeaf(root2)
    }
    
    func getLeaf(_ root: TreeNode?) -> [Int] {
        if let root = root {
            if root.left == nil && root.right == nil {
                return [root.val]
            } else {
                return getLeaf(root.left) + getLeaf(root.right)
            }
        } else {
            return []
        }
    }
}
```

## 解题思路
取出两棵树的叶子节点，比较两个数组时候相等

#树