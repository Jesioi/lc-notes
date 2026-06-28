# 637. Average of Levels in Binary Tree

- 🔗 Link：https://leetcode.com/problems/average-of-levels-in-binary-tree/description/
- 🧠 Tag：BFS
- ⭐ Level：Easy
- 📅 Date：2026-03-02

---

## Problem Statement

## Key Insights
- 

## Approach
1)
2)

## Tricky points/ Mistakes
- double division, need to cast to double before division
-

### Time and Space Complexity
- time: O(n)
- space: O(n); holds In the worst case (a complete binary tree), 
  the queue may hold up to n/2 nodes, so the space complexity is O(n).

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
    public List<Double> averageOfLevels(TreeNode root) {
        if(root == null)return new ArrayList<>();
        List<Double> ans = new ArrayList<>();
        Deque<TreeNode> stack = new ArrayDeque<>(); 
        stack.offer(root); 

        while(!stack.isEmpty()){
            int len = stack.size();
            double sum = 0.0;

            for(int i = 0; i < len; i++){
                TreeNode curr = stack.poll();
                sum += curr.val;              
                if(curr.left != null){
                    stack.offer(curr.left);
                }

                if(curr.right != null){
                    stack.offer(curr.right);
                }
            }
            ans.add(sum/len);
        }
        return ans;

    }
}


