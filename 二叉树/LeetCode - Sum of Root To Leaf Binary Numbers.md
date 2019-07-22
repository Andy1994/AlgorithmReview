# LeetCode - Sum of Root To Leaf Binary Numbers
[Sum of Root To Leaf Binary Numbers - LeetCode](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/)

## Solution
```
class Solution {
    func sumRootToLeaf(_ root: TreeNode?) -> Int {
        return getLeafString(root, value: []).map { (num) in
            return binTodec(number: num)
        }.reduce(0, +)
    }
    
    func getLeafString(_ root: TreeNode?, value: [Int]) -> [String] {
        guard let root = root else {
            return []
        }
        if root.left == nil && root.right == nil {
            return [(value + [root.val]).map{ String($0) }.joined()]
        } else {
            return getLeafString(root.left, value: value + [root.val]) + getLeafString(root.right, value: value + [root.val])
        }
    }
    
    func binTodec(number num: String) -> Int {
        var sum: Int = 0
        for c in num {
            let str = String(c)
            sum = sum * 2 + Int(str)!
        }
        return sum
    }
}
```

## 解题思路
递归取出叶子节点的值，转换成十进制相加

#树