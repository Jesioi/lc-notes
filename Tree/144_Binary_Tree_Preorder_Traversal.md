# 📌 144. Binary Tree Preorder Traversal

- 🔗 Link：https://leetcode.com/problems/binary-tree-preorder-traversal/
- 🧠 Tag：Tree / Preorder / DFS / Recursion / Stack
- ⭐ Level：Easy
- 📅 Date：2026-02-26

---

## 题意（一句话总结）

给定一棵二叉树，按 root→left→right 顺序返回前序遍历结果的所有节点值。

## 关键观察
---

## 解法思路

**前序遍历顺序：**


### Method 1：Recursion

1. 访问当前节点
2. 递归遍历左子树
3. 递归遍历右子树

### Method 2：iterate
1. 用stack存储节点，因为是preorder，stack是FILO，所以先把右子树入栈，再把左子树入栈，这样左子树就会先被访问。


## 易错点（我为什么错）
- method 2:
  - Deque generic type 应该是TreeNode而不是Integer
- method 1:
  - border case: root == null

### 时空复杂度
time: O(n) 需要访问每个节点一次
space: O(n) 最坏情况下树退化成链表，递归栈

## 代码（Java）
```java
class Solution {
    private List<Integer> ans;

    public List<Integer> preorderTraversal(TreeNode root) {
        ans = new ArrayList<>();
        preorder(root);
        return ans;
        
    }

    private void preorder(TreeNode root){
        if(root == null)return;

        ans.add(root.val);
        preorder(root.left);
        preorder(root.right);
    }
}

```java
class Solution { //iterate
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        if (root == null) return ans;

        Deque<TreeNode> stack = new ArrayDeque<>();
        stack.offerFirst(root); //第一个root先进
        while (!stack.isEmpty()) {
            TreeNode curr = stack.pollFirst();
            ans.add(curr.val);
            if (curr.right != null) {
                stack.offerFirst(curr.right);
            }

            if (curr.left != null) {
                stack.offerFirst(curr.left);
            }
        }
        return ans;
    }
}

