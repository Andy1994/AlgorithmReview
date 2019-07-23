# LeetCode - Smallest Subtree with all the Deepest Nodes
[Smallest Subtree with all the Deepest Nodes - LeetCode](https://leetcode.com/problems/smallest-subtree-with-all-the-deepest-nodes/)

## Swift Solution
```
class Solution {
    func subtreeWithAllDeepest(_ root: TreeNode?) -> TreeNode? {
        let (_, tree) = find(root)
        return tree
    }
    
    func find(_ root: TreeNode?) -> (Int, TreeNode?) {
        guard let root = root else {
            return (0, nil)
        }
        let (lDeep, lNode) = find(root.left)
        let (rDeep, rNode) = find(root.right)
        let maxDeep = max(lDeep, rDeep) + 1
        if lDeep == rDeep {
            return (maxDeep, root)
        } else if lDeep > rDeep {
            return (maxDeep, lNode)
        } else {
            return (maxDeep, rNode)
        }
    }
}
```

#树