# 2. Add Two Numbers

🔗 Link：https://leetcode.com/problems/add-two-numbers/?envType=company&envId=amazon&favoriteSlug=amazon-thirty-days

---

## Approach

- Simulate addition digit by digit while maintaining a carry.
- Maintain a dummy node for the result list, a current pointer to append new digits, and a carry from the previous addition.
- In each iteration, read one digit from each list if available, add them together with the carry, append the new digit to the result list, update the carry, and move both pointers forward.

### Complexity

Time: O(max(m,n))
Space: O(max(m,n))

## Input variation

- Linked list
- Array/List
- String

## Key point

- input 正序还是倒序

## Code (Java)

```java
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode dummy = new ListNode(0);
        ListNode cur = dummy;

        //只要任何一个链表还有node，或者carry还没处理完就继续
        while (l1 != null || l2 != null || carry != 0) { //确定好边界，这应该写l1 != null,如果写.next != null, 单个node就无法处理了
            int x = (l1 != null) ? l1.val : 0;
            int y = (l2 != null) ? l2.val : 0;

            int sum = x + y + carry;
            carry = sum / 10; //整数是要进位的


            cur.next = new ListNode(sum % 10); //余数是留下来的
            cur = cur.next; //更新指针

            if (l1 != null) {
                l1 = l1.next;
            }
            if (l2 != null) {
                l2 = l2.next;
            }

        }

        return dummy.next;
    }
}

```
