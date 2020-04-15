##### 链表区间反转

[链表区间反转，难度简单](https://leetcode-cn.com/problems/reverse-linked-list-ii/)

```js
//输入: 1->2->3->4->5->NULL, m = 2, n = 4
//输出: 1->4->3->2->5->NULL
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} m
 * @param {number} n
 * @return {ListNode}
 */
var reverseBetween = function(head, m, n) {
    var p1, p2 , p3;
    
    var nl = new ListNode(0)
    nl.next = head
    for(var i =0; i <=m ; i++) {
        nl.next = nl.next
    }
    p1 = nl;// 第一段，不需要反转
    
    var tail = p1.next
    var pre = p1.next
    var current = p1.next.next

    for(var i =m ; i <= n;i++) {
        let temp = current.next;
        current.next = pre
        pre = current
        current = temp
    }
    p1.next = pre
    tail.next = current
    return nl.next
};

var reverseBetween = function(head, m, n) {
    
};
```

