# LeetCode - Binary Tree Postorder Traversal
[Binary Tree Postorder Traversal - LeetCode](https://leetcode.com/problems/binary-tree-postorder-traversal)

## Solution
```
class Solution {
    func postorderTraversal(_ root: TreeNode?) -> [Int] {
        guard let root = root else {
            return []
        }
        return postorderTraversal(root.left) + postorderTraversal(root.right) + [root.val]
    }
}
```

#树