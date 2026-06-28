# 94. Binary Tree Inorder Traversal

- 🔗 Link：https://leetcode.com/problems/binary-tree-inorder-traversal/description/
- 🧠 Tag：Binary Tree / Inorder / DFS / Recursion / Stack
- ⭐ Level：Easy
- 📅 Date：2026-02-26

---

## Problem Statement
iterate or recursion to return all the nodes in inorder traversal order

## Key Insights
- 

## Approach
1) iterate
2) recursion

## Tricky points/ Mistakes
- 
-

### Time and Space Complexity
- time: O()
- space: O()

### Interview
1) Clarify the problem，define input, output and edge cases.
2) Approaches
3) Why it works
4) Time and space complexity

The input is the root of a binary tree
we need to return the inorder traversal result of each node to List of Integer
Inorder means we in the order of left, root, right of the subtree
The edge case is when the root is null, we should return an empty list
The key idea: go as left as possible before processing any node.
So I maintain a pointer curr, and while it’s not null, I keep pushing nodes onto the stack and move to the left child.
When I can’t go further left, I pop from the stack, visit that node, and then move to its right subtree.

## Code (Java)
```java
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>(); // 
        if(root == null) return ans;

        Deque<TreeNode> stack = new ArrayDeque<>();
        TreeNode curr = root; 

        while(curr != null || !stack.isEmpty()){
            if(curr != null){
                stack.offerFirst(curr);
                curr = curr.left;
            }else{
                curr = stack.pollFirst();
                ans.add(curr.val);
                curr = curr.right;
            }
        }
        return ans;
    }
}

