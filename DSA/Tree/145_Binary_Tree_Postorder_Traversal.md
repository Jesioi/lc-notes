# 145. Binary Tree Postorder Traversal

- 🔗 Link：https://leetcode.com/problems/binary-tree-postorder-traversal/description/
- 🧠 Tag：Binary Tree / Postorder / DFS / Recursion / Stack
- ⭐ Level：Easy
- 📅 Date：2026-02-26

---

## Problem Statement
input: TreeNode root
output: List of Integer, return all the nodes in postorder traversal order

## Key Insights
- go by direction
  - going down
    - 1) prev == null 2)curr = prev.left 3) curr = prev.right
  - going right
  - going up

## Approach
1) iteration
2) recursion

## Tricky points/ Mistakes
- compiler error, stack should be Deque<TreeNode> instead of Deque<Integer>
- when answer added, should add curr.val instead of curr itself

### Time and Space Complexity
- time: O()
- space: O()

### Interview
1) Clarify the problem，define input, output and edge cases.
2) Approaches
3) Why it works
4) Time and space complexity



## Code (Java)
```java
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        if(root == null) return ans; 

        Deque<TreeNode> stack = new ArrayDeque<>();
        stack.offerFirst(root); 
        
        TreeNode prev = null;
        while(!stack.isEmpty()){
            TreeNode curr = stack.peekFirst();
            // go by direction: down
            // 1) prev == null 2)curr = prev.left 3) curr = prev.right 
            // go by direction: right
            // go by direction: up
            // stack simulation: 
            if(prev == null || curr == prev.left || curr == prev.right){
                if(curr.left != null){
                    stack.offerFirst(curr.left);  
                }else if(curr.right != null){
                    stack.offerFirst(curr.right); 
                }else{
                    ans.add(stack.pollFirst().val); 
                }
            }else if(prev == curr.left){ 
                if(curr.right != null){
                    stack.offerFirst(curr.right);
                }else{
                    ans.add(stack.pollFirst().val);
                }
            }else{
                ans.add(stack.pollFirst().val); 
            }
            prev = curr;
        }
        return ans;
    }
}

// postorder = 132654
// stack ||     

//       4
//    /    \
//   2       5
// /   \   /   \ 
// 1    3       6   

