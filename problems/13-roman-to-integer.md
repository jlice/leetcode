## 13. Roman to Integer - 罗马数字转整数

<!--If you want to use the English description, use `question.content` instead-->

<p>罗马数字包含以下七种字符:&nbsp;<code>I</code>，&nbsp;<code>V</code>，&nbsp;<code>X</code>，&nbsp;<code>L</code>，<code>C</code>，<code>D</code>&nbsp;和&nbsp;<code>M</code>。</p>

<pre><strong>字符</strong>          <strong>数值</strong>
I             1
V             5
X             10
L             50
C             100
D             500
M             1000</pre>

<p>例如， 罗马数字 2 写做&nbsp;<code>II</code>&nbsp;，即为两个并列的 1。12 写做&nbsp;<code>XII</code>&nbsp;，即为&nbsp;<code>X</code>&nbsp;+&nbsp;<code>II</code>&nbsp;。 27 写做&nbsp;&nbsp;<code>XXVII</code>, 即为&nbsp;<code>XX</code>&nbsp;+&nbsp;<code>V</code>&nbsp;+&nbsp;<code>II</code>&nbsp;。</p>

<p>通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做&nbsp;<code>IIII</code>，而是&nbsp;<code>IV</code>。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为&nbsp;<code>IX</code>。这个特殊的规则只适用于以下六种情况：</p>

<ul>
	<li><code>I</code>&nbsp;可以放在&nbsp;<code>V</code>&nbsp;(5) 和&nbsp;<code>X</code>&nbsp;(10) 的左边，来表示 4 和 9。</li>
	<li><code>X</code>&nbsp;可以放在&nbsp;<code>L</code>&nbsp;(50) 和&nbsp;<code>C</code>&nbsp;(100) 的左边，来表示 40 和&nbsp;90。&nbsp;</li>
	<li><code>C</code>&nbsp;可以放在&nbsp;<code>D</code>&nbsp;(500) 和&nbsp;<code>M</code>&nbsp;(1000) 的左边，来表示&nbsp;400 和&nbsp;900。</li>
</ul>

<p>给定一个罗马数字，将其转换成整数。输入确保在 1&nbsp;到 3999 的范围内。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>&nbsp;&quot;III&quot;
<strong>输出:</strong> 3</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>&nbsp;&quot;IV&quot;
<strong>输出:</strong> 4</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong>&nbsp;&quot;IX&quot;
<strong>输出:</strong> 9</pre>

<p><strong>示例&nbsp;4:</strong></p>

<pre><strong>输入:</strong>&nbsp;&quot;LVIII&quot;
<strong>输出:</strong> 58
<strong>解释:</strong> L = 50, V= 5, III = 3.
</pre>

<p><strong>示例&nbsp;5:</strong></p>

<pre><strong>输入:</strong>&nbsp;&quot;MCMXCIV&quot;
<strong>输出:</strong> 1994
<strong>解释:</strong> M = 1000, CM = 900, XC = 90, IV = 4.</pre>



-----

题目标签：Math / String

题目链接：[LeetCode](https://leetcode.com/problems/roman-to-integer/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/roman-to-integer/description/)

## 题解

罗马数字转阿拉伯数字。碰到`IX`这种，可以先减去`I`再加上`X`，这样就不需要用skip标志位了。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 212  ms | N/A |

```python3
class Solution:
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        d = {
            'I':             1,
            'V':             5,
            'X':             10,
            'L':             50,
            'C':             100,
            'D':             500,
            'M':             1000,
        }
        num = 0
        skip = False
        for i, c in enumerate(s):
            if skip:
                skip = False
                continue
            if i == len(s) - 1:
                num += d[c]
            else:
                if d[c] < d[s[i+1]]:
                    num += d[s[i+1]] - d[c]
                    skip = True
                else:
                    num += d[c]
        return num
```