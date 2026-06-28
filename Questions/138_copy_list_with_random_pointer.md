# 138. Copy List with Random Pointer

🔗 Link：https://leetcode.com/problems/copy-list-with-random-pointer/description/?envType=company&envId=amazon&favoriteSlug=amazon-thirty-days

---

## Approach

- hashmap

### Complexity

time: O(n)
space: O(n)

---

## Approach

- interleave each copied node with its original node. This allows me to locate the copied version of any node in O(1) time.

### Complexity

time: O(n)
space: O(1)

## Input variation

---

## Code

```java
//空间优化版
class Solution {
    public Node copyRandomList(Node head) {
        if (head == null) return null;

        Node cur = head;

        // 1. Copy each node and insert it right after original node
        while (cur != null) {
            Node copy = new Node(cur.val);

            copy.next = cur.next;
            cur.next = copy;

            cur = copy.next;
        }

        // 2. Assign random pointers
        cur = head;
        while (cur != null) {
            Node copy = cur.next;

            if (cur.random != null) {
                copy.random = cur.random.next;
            }

            cur = copy.next;
        }

        // 3. Separate original list and copied list
        cur = head;
        Node newHead = head.next;

        while (cur != null) {
            Node copy = cur.next;

            cur.next = copy.next;

            if (copy.next != null) {
                copy.next = copy.next.next;
            }

            cur = cur.next;
        }

        return newHead;
    }
}




```
