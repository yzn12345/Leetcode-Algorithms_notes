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
    public ListNode deleteDuplicates(ListNode head) {
        
        
        ListNode cur = head;
        ListNode dummy = cur;
        
        while (cur != null) {
            if (cur.next == null) {
                break;
            }
            if (cur.next.val == cur.val) {
                cur.next = cur.next.next;
                
            }
            else if (cur.next.val != cur.val) {
                cur = cur.next;
                
            }
        }
        return dummy;
        
    }
}
```

与去除数组内重复类似， 如果当前和当前后一位不同，移动index; 反之则更改当前.next = .next.next且不移动index。