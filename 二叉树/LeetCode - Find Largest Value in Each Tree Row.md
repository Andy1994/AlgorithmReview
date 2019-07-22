# LeetCode - Find Largest Value in Each Tree Row
[Find Largest Value in Each Tree Row - LeetCode](https://leetcode.com/problems/find-largest-value-in-each-tree-row/)

## Solution
```
class Solution {
    func largestValues(_ root: TreeNode?) -> [Int] {
        var dict = [Int: [Int]]()
        traversing(root, 0, &dict)
        var result = [Int]()
        for key in dict.keys.sorted() {
            result.append(dict[key]!.max()!)
        }
        return result
    }
    
    func traversing(_ root: TreeNode?, _ deep: Int, _ dict: inout [Int: [Int]]) {
        guard let root = root else {
            return
        }
        if let array = dict[deep] {
            dict[deep] = array + [root.val]
        } else {
            dict[deep] = [root.val]
        }
        traversing(root.left, deep + 1, &dict)
        traversing(root.right, deep + 1, &dict)
    }
}
```

#树