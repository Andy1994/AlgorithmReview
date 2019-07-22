# LeetCode - Insert into a Binary Search Tree
[Insert into a Binary Search Tree - LeetCode](https://leetcode.com/problems/insert-into-a-binary-search-tree/)

## Solution
```
class Solution {
    func insertIntoBST(_ root: TreeNode?, _ val: Int) -> TreeNode? {
        var root = root
        insertIntoBST(&root, val)
        return root
    }
    
    func insertIntoBST(_ root: inout TreeNode?, _ val: Int) {
        guard let root = root else {
            return
        }
        if val < root.val {
            if root.left == nil {
                root.left = TreeNode(val)
            } else {
                insertIntoBST(&root.left, val)
            }
        } else {
            if root.right == nil {
                root.right = TreeNode(val)
            } else {
                insertIntoBST(&root.right, val)
            }
        }
    }
}
```

 #树