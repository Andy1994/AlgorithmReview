# LeetCode - Range Sum of BST
[Range Sum of BST - LeetCode](https://leetcode.com/problems/range-sum-of-bst/)

## Solution
```
class Solution {
    func rangeSumBST(_ root: TreeNode?, _ L: Int, _ R: Int) -> Int {
        if let root = root {
            if L > root.val {
                return rangeSumBST(root.right, L, R)
            } else if R < root.val {
                return rangeSumBST(root.left, L, R)
            } else {
                var sum = 0
                sum += rangeSumBST(root.left, L, R)
                sum += root.val
                sum += rangeSumBST(root.right, L, R)
                return sum
            }
        } else {
            return 0
        }
    }
}
```

#树