# [1784. 检查二进制字符串字段](https://leetcode.cn/problems/check-if-binary-string-has-at-most-one-segment-of-ones/)

## 题目描述

给你一个二进制字符串 `s` ，该字符串 **不含前导零** 。

如果 `s` 包含 **零个或一个由连续的 '1' 组成的字段** ，返回 `true`​​​ 。否则，返回 `false` 

如果 `s` 中 **由连续若干个 '1' 组成的字段 数量不超过 1**，返回 `true`​​​ 。否则，返回 `false` 

**示例1：**

```
输入：s = "1001"
输出：false
解释：由连续若干个 '1' 组成的字段数量为 2，返回 false
```

示例2：

```
输入：s = "110"
输出：true
```

**提示：**

- `1 <= s.length <= 100`
- `s[i]`​​​​ 为 `'0'` 或 `'1'`
- `s[0]` 为 `'1'`

## 解决方案

### 方法一：简单模拟

题目已经明确给定`s[0] = '1'`，所以我们只需要找出`s`中的第一个字符`'0'`的下标。

- 若字符串`s`中不存在`'0'`，那么一定全为`'1'`，返回`True`

- 若字符串`s`中存在`'0'`，但是在它的后面不存在`'1'`，说明`s`中只有一个由连续的`'1'`组成的字段（因为`s[0] = '1'`），返回`True`

若不满足以上两点条件，直接返回`False`

#### Python3

```python
class Solution:
    def checkOnesSegment(self, s: str) -> bool:
        idx = s.find('0')
        if idx == -1 or '1' not in s[idx:]:
            return True
        return False
```

采用三元表达式写法

```python
class Solution:
    def checkOnesSegment(self, s: str) -> bool:
        return True if s.find('0') == -1 or '1' not in s[s.find('0'):] else False
```

#### Java

```java
class Solution {
    public boolean checkOnesSegment(String s) {
        int idx = s.indexOf("0");
        if(idx == -1 || s.substring(idx).indexOf("1") == -1) return true;
        return false;
    }
}  
```

采用三元表达式写法

```java
class Solution {
    public boolean checkOnesSegment(String s) {
        return s.indexOf("0") == -1 || s.substring(s.indexOf("0")).indexOf("1") == -1 ? true : false;
    }
}  
```
