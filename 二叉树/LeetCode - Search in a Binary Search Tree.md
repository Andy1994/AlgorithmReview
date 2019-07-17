# LeetCode - Search in a Binary Search Tree
#树
[Search in a Binary Search Tree - LeetCode](https://leetcode.com/problems/search-in-a-binary-search-tree/)

## Solution
```
class Solution {
    func searchBST(_ root: TreeNode?, _ val: Int) -> TreeNode? {
        if let root = root {
            if root.val == val {
                return root
            } else {
                if let left = root.left, let result = searchBST(left, val) {
                    return result
                }
                if let right = root.right, let result = searchBST(right, val) {
                    return result
                }
                return nil
            }
        } else {
            return nil
        }
    }
}
```
