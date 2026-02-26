# 102. Binary Tree Level Order Traversal

- 🔗 Link：https://leetcode.com/problems/binary-tree-level-order-traversal/description/
- 🧠 Tag：BFS / Tree / Queue
- ⭐ Level：Medium
- 📅 Date：2026-02-26

---

## Problem Statement
Given the root of a binary tree, return the level order traversal of its nodes' values 
(i.e., from left to right, level by level).

## Key Insights
- BFS

## Approach
1) iterate
2) recursion

## Tricky points/ Mistakes
- 
-

### Time and Space Complexity
- time: O(n)
- space: O(n)

### Interview
1) Clarify the problem，define input, output and edge cases.
2) Approaches
3) Why it works
4) Time and space complexity

## Code (Java)
```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> ans = new ArrayList<>();
        if(root == null)return ans;

        Deque<TreeNode> queue = new ArrayDeque<>();
        queue.offer(root);
 
        while(!queue.isEmpty()){
            List<Integer> res = new ArrayList<>();
            int len = queue.size();

            while (len > 0){
                TreeNode temp = queue.poll();
                res.add(temp.val);

                if(temp.left != null){
                    queue.offer(temp.left);
                }

                if(temp.right != null){
                    queue.offer(temp.right);
                }
                len--;

            }
            ans.add(res);
        }
        return ans;
    }
}
