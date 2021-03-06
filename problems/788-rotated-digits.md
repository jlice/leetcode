## 788. Rotated Digits - 旋转数字

<!--If you want to use the English description, use `question.content` instead-->

<p>我们称一个数 X 为好数, 如果它的每位数字逐个地被旋转 180 度后，我们仍可以得到一个有效的，且和 X 不同的数。要求每位数字都要被旋转。</p>

<p>如果一个数的每位数字被旋转以后仍然还是一个数字，&nbsp;则这个数是有效的。0, 1, 和 8 被旋转后仍然是它们自己；2 和 5 可以互相旋转成对方；6 和 9 同理，除了这些以外其他的数字旋转以后都不再是有效的数字。</p>

<p>现在我们有一个正整数&nbsp;<code>N</code>, 计算从&nbsp;<code>1</code> 到&nbsp;<code>N</code> 中有多少个数&nbsp;X 是好数？</p>

<pre>
<strong>示例:</strong>
<strong>输入:</strong> 10
<strong>输出:</strong> 4
<strong>解释:</strong> 
在[1, 10]中有四个好数： 2, 5, 6, 9。
注意 1 和 10 不是好数, 因为他们在旋转之后不变。
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li>N&nbsp;的取值范围是&nbsp;<code>[1, 10000]</code>。</li>
</ul>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/rotated-digits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/rotated-digits/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 156  ms | N/A |

```python3
class Solution:
    def rotatedDigits(self, N):
        """
        :type N: int
        :rtype: int
        """
        num = 0
        for i in range(1, N+1):
            s = str(i)
            if any(('3' in s, '4' in s, '7' in s)):
                continue
            elif any(('2' in s, '5' in s, '6' in s, '9' in s)):
                num += 1
        return num
```
