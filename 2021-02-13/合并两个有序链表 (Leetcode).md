```Java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        
        ListNode left = l1;
        ListNode right = l2;
        ListNode head = new ListNode(-1);
        ListNode dummy = head;
        while (left != null && right != null) {
            head.next = left.val > right.val ? new ListNode(right.val) : new ListNode(left.val);
            
            if (left.val > right.val) {
                right = right.next;
            }
            else if (left.val <= right.val) {
                left = left.next;
            }
            head = head.next;
            
        }
        while(left!=null) {
            head.next = left;
            left = left.next;
            head = head.next;
        }
        while(right!=null) {
            head.next = right;
            right = right.next;
            head = head.next;
        }
        return dummy.next;
    }
}
```

需要注意的是要用else if而不是if 否则可能进入两个condition blocks。