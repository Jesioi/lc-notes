### 核心骨架

preorder & inorder 的核心骨架是一样的：
- 区别只在visit 在哪里

postorder:
1) two stacks: 1 for nodes, 1 for visited status
2) one stack + prev pointer: go by direction

interview:
- use stack to simulate the recursive call stack.

```java
while (curr != null || !stack.isEmpty()) {
    if (curr != null) {
        stack.push(curr);
        curr = curr.left;   // 或 right
    } else {
        curr = stack.pop();
        // visit here
        curr = curr.right;  // 或 left
    }
}

public List<Integer> preorderTraversal(TreeNode root) {
    List<Integer> ans = new ArrayList<>();
    Deque<TreeNode> stack = new ArrayDeque<>();
    TreeNode curr = root;

    while (curr != null || !stack.isEmpty()) {
        if (curr != null) {
            ans.add(curr.val);   // ⭐ VISIT HERE
            stack.push(curr);
            curr = curr.left;
        } else {
            curr = stack.pop();
            curr = curr.right;
        }
    }
    return ans;
}

public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> ans = new ArrayList<>();
    Deque<TreeNode> stack = new ArrayDeque<>();
    TreeNode curr = root;

    while (curr != null || !stack.isEmpty()) {
        if (curr != null) {
            stack.push(curr);
            curr = curr.left;
        } else {
            curr = stack.pop();
            ans.add(curr.val);   // ⭐ VISIT HERE
            curr = curr.right;
        }
    }
    return ans;
}

public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> ans = new ArrayList<>();
    if (root == null) return ans;

    Deque<TreeNode> stack1 = new ArrayDeque<>();
    Deque<TreeNode> stack2 = new ArrayDeque<>();

    stack1.push(root);

    while (!stack1.isEmpty()) {
        TreeNode curr = stack1.pop();
        stack2.push(curr);

        if (curr.left != null) stack1.push(curr.left);
        if (curr.right != null) stack1.push(curr.right);
    }

    while (!stack2.isEmpty()) {
        ans.add(stack2.pop().val);
    }

    return ans;
}

public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> ans = new ArrayList<>();
    if (root == null) return ans;

    Deque<TreeNode> stack = new ArrayDeque<>();
    stack.push(root);

    TreeNode prev = null;

    while (!stack.isEmpty()) {
        TreeNode curr = stack.peek();

        if (prev == null || prev.left == curr || prev.right == curr) {
            if (curr.left != null) {
                stack.push(curr.left);
            } else if (curr.right != null) {
                stack.push(curr.right);
            } else {
                stack.pop();
                ans.add(curr.val);
            }
        } else if (curr.left == prev) {
            if (curr.right != null) {
                stack.push(curr.right);
            } else {
                stack.pop();
                ans.add(curr.val);
            }
        } else {
            stack.pop();
            ans.add(curr.val);
        }

        prev = curr;
    }

    return ans;
}


