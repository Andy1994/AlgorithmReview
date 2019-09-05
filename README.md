# AlgorithmReview

## * 链表
### 1.单链表反转 
```
public ListNode reverse(ListNode head) {
    if (head == null || head.next == null) {
        return head;
    }
    ListNode preNode = null;
    ListNode nextNode = null;
    while (head != null){
        nextNode = head.next;
        head.next = preNode;
        preNode = head;
        head = nextNode;
    }
    return preNode;
}
```
### 2.链表中环的检测
```
// 快慢指针解法
public boolean detectLoop(ListNode head) {
    ListNode pSlow = head, pFast = head;
    boolean detectFlag = false;
    if (head.next == null) {
        return detectFlag;
    }
    while (true) {
        pSlow = pSlow.next;
        pFast = pFast.next.next;
        if (pFast == null) {
            break;
        }
        if (pSlow == pFast) {
            detectFlag = true;
            break;
        }
    }
    return detectFlag;
}
```
### 3.两个有序的链表合并
```
// 遍历解法
// 同时不断遍历两个链表，取出小的追加到新的头节点后，直至两者其中一个为空
// 再将另一者追加的新链表最后
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(-1);
    ListNode curNode = dummy;
    while (l1 != null && l2 != null) {
        if (l1.val <= l2.val) {
            curNode.next = l1;
            l1 = l1.next;
        } else {
            curNode.next = l2;
            l2 = l2.next;
        }
        curNode = curNode.next;
    }
    curNode.next = (l1 != null) ? l1 : l2;
    return dummy.next;
}
```
### 4.删除链表倒数第n个结点
```
public ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode preNode = head;
    ListNode curNode = head;
    // 前指针先走nbu
    for (int i = 0; i < n; i++) {
        curNode = curNode.next;
    }
    if (curNode == null) {
        return preNode.next;
    }
    // 前后指针同时走，走到尾部，preNode.next就是需要删除的节点
    while (curNode.next != null) {
        preNode = preNode.next;
        curNode = curNode.next;
    }
    // 删除节点
    preNode.next = preNode.next.next;
    return head;
}
```
### 5.求链表的中间结点
```
// 使用快慢指针，一个指针每次只遍历一个节点，另一个速度为2倍，当快指针指向表尾时，慢指针指向中间节点
public ListNode middleNode(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}
```

## * 树
1. 二叉树
* [二叉树：前(先)序、中序、后序遍历](https://github.com/Andy1994/AlgorithmReview/blob/master/%E4%BA%8C%E5%8F%89%E6%A0%91/%E4%BA%8C%E5%8F%89%E6%A0%91%EF%BC%9A%E5%89%8D(%E5%85%88)%E5%BA%8F%E3%80%81%E4%B8%AD%E5%BA%8F%E3%80%81%E5%90%8E%E5%BA%8F%E9%81%8D%E5%8E%86.md)
* [LeetCode - Search in a Binary Search Tree](https://github.com/Andy1994/AlgorithmReview/blob/master/%E4%BA%8C%E5%8F%89%E6%A0%91/LeetCode%20-%20Search%20in%20a%20Binary%20Search%20Tree.md)
