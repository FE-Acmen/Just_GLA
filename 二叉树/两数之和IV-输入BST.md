## 两数之和IV-输入BST

**简单**

题目：给定一个二叉搜索树 `root` 和一个目标结果 `k`，如果 BST 中存在两个元素且它们的和等于给定的目标结果，则返回 `true`。

示例：

![示例](D:\study\算法\Just_GLA\assets\images\sum_tree_1.jpg)

```
输入: root = [5,3,6,2,4,null,7], k = 9
输出: true
```

题解：

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} k
 * @return {boolean}
 */
var findTarget = function(root, k) {
    let set = new Set();
    const preOrder = (tree, m, hashset) => {
        if(tree === null) {
            return false;
        }
        if(hashset.has(m - tree.val)) {
            return true;
        }
        hashset.add(tree.val);
        return preOrder(tree.left, m, hashset) || preOrder(tree.right, m, hashset);
    }
    return preOrder(root, k, set);
};
```

