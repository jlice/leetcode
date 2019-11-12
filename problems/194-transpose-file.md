## 194. Transpose File - 转置文件

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个文件&nbsp;<code>file.txt</code>，转置它的内容。</p>

<p>你可以假设每行列数相同，并且每个字段由&nbsp;<code>&#39; &#39;</code> 分隔.</p>

<p><strong>示例:</strong></p>

<p>假设&nbsp;<code>file.txt</code>&nbsp;文件内容如下：</p>

<pre>name age
alice 21
ryan 30
</pre>

<p>应当输出：</p>

<pre>name alice ryan
age 21 30
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/transpose-file/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/transpose-file/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| bash  | 16  ms | N/A |

```bash
# Read from the file file.txt and print its transposed content to stdout.

# using awk for this purpose
awk '
    {
        for(i=1; i<=NF; i++)
        {   
            if(line[i] == "")
            {
                line[i] = $i
            }
            else
            {
                line[i] = line[i]" "$i
            }
        }
    }
    END{
         for(i=1; i<=NF; i++)
         {
             print line[i]
         }
       }
    ' file.txt
```