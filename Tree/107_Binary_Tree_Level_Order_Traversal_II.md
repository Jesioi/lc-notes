# 107. Binary Tree Level Order Traversal II

- 🔗 Link：https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/
- 🧠 Tag：BFS, Tree
- ⭐ Level：Medium
- 📅 Date：2024-06-11

---

## Problem Statement
return all nodes of the tree from bottom to top, left to right

## Key Insights
- bfs

## Approach
1) reverse result of bfs top to bottom
2) use stack to store result

## Tricky points/ Mistakes

---

### Time and Space Complexity
- time: O(n)
- space: O(n)

### Interview
1) Clarify the problem，define input, output and edge cases.
2) Approaches
3) Why it works
4) Time and space complexity
-
-

## Code (Java)
```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ans = new ArrayList<>();
        if (root == null) return ans;

        Deque<TreeNode> queue = new ArrayDeque<>();
        Deque<List<Integer>> stack = new ArrayDeque<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            List<Integer> res = new ArrayList<>();
            int len = queue.size();
            
            while (len > 0) {
                TreeNode temp = queue.poll();
                res.add(temp.val);

                if (temp.left != null) {
                    queue.offer(temp.left);
                }

                if (temp.right != null) {
                    queue.offer(temp.right);
                }
                len--;
            }
            stack.push(res);
        }

        while(!stack.isEmpty()){
            ans.add(stack.pop());
        }
        return ans;
    }
}

