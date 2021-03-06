## 443. String Compression - 压缩字符串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一组字符，使用<a href="https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95">原地算法</a>将其压缩。</p>

<p>压缩后的长度必须始终小于或等于原数组长度。</p>

<p>数组的每个元素应该是长度为1&nbsp;的<strong>字符</strong>（不是 int 整数类型）。</p>

<p>在完成<a href="https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95">原地</a><strong>修改输入数组</strong>后，返回数组的新长度。</p>

<p>&nbsp;</p>

<p><strong>进阶：</strong><br />
你能否仅使用O(1) 空间解决问题？</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>
[&quot;a&quot;,&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;c&quot;,&quot;c&quot;,&quot;c&quot;]

<strong>输出：</strong>
返回6，输入数组的前6个字符应该是：[&quot;a&quot;,&quot;2&quot;,&quot;b&quot;,&quot;2&quot;,&quot;c&quot;,&quot;3&quot;]

<strong>说明：</strong>
&quot;aa&quot;被&quot;a2&quot;替代。&quot;bb&quot;被&quot;b2&quot;替代。&quot;ccc&quot;被&quot;c3&quot;替代。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>
[&quot;a&quot;]

<strong>输出：</strong>
返回1，输入数组的前1个字符应该是：[&quot;a&quot;]

<strong>说明：</strong>
没有任何字符串被替代。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>
[&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;,&quot;b&quot;]

<strong>输出：</strong>
返回4，输入数组的前4个字符应该是：[&quot;a&quot;,&quot;b&quot;,&quot;1&quot;,&quot;2&quot;]。

<strong>说明：</strong>
由于字符&quot;a&quot;不重复，所以不会被压缩。&quot;bbbbbbbbbbbb&quot;被&ldquo;b12&rdquo;替代。
注意每个数字在数组中都有它自己的位置。
</pre>

<p><strong>注意：</strong></p>

<ol>
	<li>所有字符都有一个ASCII值在<code>[35, 126]</code>区间内。</li>
	<li><code>1 &lt;= len(chars) &lt;= 1000</code>。</li>
</ol>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/string-compression/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/string-compression/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 72  ms | N/A |

```python3
class Solution:
    def compress(self, chars):
        """
        :type chars: List[str]
        :rtype: int
        """
        n = len(chars)
        pre, cnt = '', 0
        for _ in range(n):
            if pre:
                tmp = chars.pop()
                if tmp == pre:
                    cnt += 1
                else:
                    if cnt > 1:
                        for c in str(cnt)[::-1]:
                            chars.insert(0, c)
                    chars.insert(0, pre)
                    pre = tmp
                    cnt = 1
            else:
                pre = chars.pop()
                cnt = 1
        if cnt > 1:
            for c in str(cnt)[::-1]:
                chars.insert(0, c)
        chars.insert(0, pre)
        return len(chars)
```
