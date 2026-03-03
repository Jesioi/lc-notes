# 429. N-ary Tree Level Order Traversal

- 🔗 Link：https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/
- 🧠 Tag：
- ⭐ Level：Medium
- 📅 Date：2026-03-02

---

## Problem Statement

## Key Insights
- Node constructor: 
- Node(int _val, List<Node> _children) {
    val = _val;
    children = _children;
}
- 一个node 对应的children是一个list，里面包含了所有的child node

## Approach
1)
2)

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
-
-


## Code (Java)
```java
class Solution {
    public List<List<Integer>> levelOrder(Node root) {
        if(root == null) return new ArrayList<>(); 
        List<List<Integer>> ans = new ArrayList<>();

        Deque<Node> stack = new ArrayDeque<>();
        stack.offer(root);

        while(!stack.isEmpty()){
            int len = stack.size();
            List<Integer> level = new ArrayList<>();

            for (int i = 0; i < len; i++){
                Node curr = stack.poll();

                level.add(curr.val);
                List<Node> children = curr.children;
                if(children == null || children.size() == 0){ //对于当前node来说他是否有list of node(孩子集)
                    continue;
                }
                for ( Node child : children){ 
                    if(child != null){
                        stack.offer(child);
                    }
                }
            }
            ans.add(level);

        }
        return ans;
    }
}


