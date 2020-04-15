##### 206反转链表

[反转链表，难度简单](https://leetcode-cn.com/problems/reverse-linked-list/)

```js
//输入: 1->2->3->4->5->NULL
//输出: 5->4->3->2->1->NULL
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function(head) {
	var pre = null , current = head;
  while(current) {
    var temp = current.next
    current.next = pre
    pre = current
    current = temp
  }
  return pre
};

var reverseList = function(head) {
		var rever = (pre , current) => {
      	if(!current) return pre
      	let next = current.next
      	current.next = pre
        return rever(current,next)
    }
  	return rever(null,head)
};


```

