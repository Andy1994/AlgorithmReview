# LeetCode - Univalued Binary Tree
[Univalued Binary Tree - LeetCode](https://leetcode.com/problems/univalued-binary-tree/)

## Solution
```
class Solution {
    func isUnivalTree(_ root: TreeNode?) -> Bool {
        if let root = root {
            return isUnivalTree(root, root.val)
        } else {
            return true
        }
    }
    
    func isUnivalTree(_ root: TreeNode?, _ val: Int) -> Bool {
        if let root = root {
            if val == root.val && isUnivalTree(root.left, val) && isUnivalTree(root.right, val) {
                return true
            } else {
                return false
            }
        } else {
            return true
        }
    }
}
```
