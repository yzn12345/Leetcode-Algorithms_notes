## 尝试1

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
        if (head == null) {return null;}
        HashSet<Integer> set = new HashSet<>();
        ListNode cur = head;
        ListNode dummy = cur;
        while (cur.next != null) {
            set.add(cur.val);
            if (set.contains(cur.next.val)) {
                cur.next = cur.next == null ? cur.next : cur.next.next;
              
            
            }
            else {  
                cur = cur.next == null ? cur : cur.next;
            }
        }
        return dummy;
    }
}
```

## 尝试2

- 发现不需要使用hashset，一次遍历即可

- 原理：如果cur.val等于cur.next.val，不挪动当前指针，只把cur.next分配为cur.next.next；如果不等于，再挪动当前指针：cur = cur.next;

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
        if (head == null) {return null;}
    
        ListNode cur = head;
        ListNode dummy = cur;
        while (cur != null) {
            if (cur.next == null) {
                return dummy;
            }
            
            if (cur.val == cur.next.val) {
                cur.next = cur.next.next;
              
            
            }
            else {  
                cur = cur.next;
            }
        }
        return dummy;
    }
}
```