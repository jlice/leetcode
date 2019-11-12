## 173. Binary Search Tree Iterator - 二叉搜索树迭代器

<!--If you want to use the English description, use `question.content` instead-->

<p>实现一个二叉搜索树迭代器。你将使用二叉搜索树的根节点初始化迭代器。</p>

<p>调用 <code>next()</code> 将返回二叉搜索树中的下一个最小的数。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/25/bst-tree.png" style="height: 178px; width: 189px;"></strong></p>

<pre>BSTIterator iterator = new BSTIterator(root);
iterator.next();    // 返回 3
iterator.next();    // 返回 7
iterator.hasNext(); // 返回 true
iterator.next();    // 返回 9
iterator.hasNext(); // 返回 true
iterator.next();    // 返回 15
iterator.hasNext(); // 返回 true
iterator.next();    // 返回 20
iterator.hasNext(); // 返回 false</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>next()</code>&nbsp;和&nbsp;<code>hasNext()</code>&nbsp;操作的时间复杂度是&nbsp;O(1)，并使用&nbsp;O(<em>h</em>) 内存，其中&nbsp;<em>h&nbsp;</em>是树的高度。</li>
	<li>你可以假设&nbsp;<code>next()</code>&nbsp;调用总是有效的，也就是说，当调用 <code>next()</code>&nbsp;时，BST 中至少存在一个下一个最小的数。</li>
</ul>



-----

题目标签：Stack / Tree / Design

题目链接：[LeetCode](https://leetcode.com/problems/binary-search-tree-iterator/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-search-tree-iterator/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 60  ms | 52.6 MB |

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class BSTIterator {
    Stack<TreeNode> stk = new Stack<>();
    
    public BSTIterator(TreeNode root) {
        while (root != null) {
            stk.push(root);
            root = root.left;
        }
    }
    
    /** @return the next smallest number */
    public int next() {
        TreeNode t = stk.pop();
        int val = t.val;
        t = t.right;
        while (t != null) {
            stk.push(t);
            t = t.left;
        }
        return val;
    }
    
    /** @return whether we have a next smallest number */
    public boolean hasNext() {
        return !stk.empty();
    }
}

/**
 * Your BSTIterator object will be instantiated and called as such:
 * BSTIterator obj = new BSTIterator(root);
 * int param_1 = obj.next();
 * boolean param_2 = obj.hasNext();
 */
```