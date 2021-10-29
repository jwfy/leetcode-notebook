### [剑指 Offer 50\. 第一个只出现一次的字符](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

Difficulty: **简单**


在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

**示例 1:**

```
输入：s = "abaccdeff"
输出：'b'
```

**示例 2:**

```
输入：s = "" 
输出：' '
```

**限制：**

`0 <= s 的长度 <= 50000`


#### Solution

Language: ****

```java
class Solution {
    public char firstUniqChar(String s) {
        int[] nums = new int[26];
        int[] idxs = new int[26];
        char[] cs = s.toCharArray();
        for(int i=0;i<cs.length;i++) {
            nums[cs[i]-'a'] += 1;
            idxs[cs[i]-'a'] = i;
        }
        int idx = s.length()+1;
        int res = -1;
        for(int i=0;i<26;i++) {
            if (nums[i] == 1 && idx > idxs[i]) {
                idx = idxs[i];
                res = i;
            }
        }
        return res == -1 ? ' ' : (char)(res + 'a');
    }
}
```