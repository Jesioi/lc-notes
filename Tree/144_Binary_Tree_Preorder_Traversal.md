# 📌 144. Binary Tree Preorder Traversal

- 🔗 链接：https://leetcode.com/problems/binary-tree-preorder-traversal/
- 🧠 标签：Tree / Preorder / DFS / Recursion / Stack
- ⭐ 难度：Easy
- 📅 练习日期：2026-02-26

---

## 题意（一句话总结）

给定一棵二叉树，按 root→left→right 顺序返回前序遍历结果的所有节点值。

## 关键观察
---

## 解法思路

**前序遍历顺序：**

可以用两种方法实现：

### 方法一：递归（最直观）

1. 访问当前节点
2. 递归遍历左子树
3. 递归遍历右子树

## 易错点（我为什么错）
- 
- 边界：

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

