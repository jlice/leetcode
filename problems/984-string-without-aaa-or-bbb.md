## 984. String Without AAA or BBB - 不含 AAA 或 BBB 的字符串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个整数&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>，返回<strong>任意</strong>字符串 <code>S</code>，要求满足：</p>

<ul>
	<li><code>S</code> 的长度为&nbsp;<code>A + B</code>，且正好包含&nbsp;<code>A</code>&nbsp;个 <code>&#39;a&#39;</code>&nbsp;字母与&nbsp;<code>B</code>&nbsp;个 <code>&#39;b&#39;</code>&nbsp;字母；</li>
	<li>子串&nbsp;<code>&#39;aaa&#39;</code>&nbsp;没有出现在&nbsp;<code>S</code>&nbsp;中；</li>
	<li>子串&nbsp;<code>&#39;bbb&#39;</code> 没有出现在&nbsp;<code>S</code>&nbsp;中。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = 1, B = 2
<strong>输出：</strong>&quot;abb&quot;
<strong>解释：</strong>&quot;abb&quot;, &quot;bab&quot; 和 &quot;bba&quot; 都是正确答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = 4, B = 1
<strong>输出：</strong>&quot;aabaa&quot;</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>0 &lt;= A &lt;= 100</code></li>
	<li><code>0 &lt;= B &lt;= 100</code></li>
	<li>对于给定的 <code>A</code> 和 <code>B</code>，保证存在满足要求的 <code>S</code>。</li>
</ol>



-----

题目标签：Greedy

题目链接：[LeetCode](https://leetcode.com/problems/string-without-aaa-or-bbb/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/string-without-aaa-or-bbb/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 3  ms | 37 MB |

```java
class Solution {
    public String strWithout3a3b(int A, int B) {
        if (A == 0) {
            return new String(new char[B]).replace('\0', 'b');
        }
        if (B == 0) {
            return new String(new char[A]).replace('\0', 'a');
        }
        if (A == B) {
            return new String(new char[A * 2]).replace("\0\0", "ab");
        } else {
            if (A > B) {
                return "aab" + strWithout3a3b(A - 2, B - 1);
            } else {
                return "bba" + strWithout3a3b(A - 1, B - 2);
            }
        }
    }
}
```