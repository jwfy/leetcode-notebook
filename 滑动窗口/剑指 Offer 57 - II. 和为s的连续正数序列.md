### [剑指 Offer 57 - II. 和为s的连续正数序列](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

Difficulty: **简单**


输入一个正整数 `target` ，输出所有和为 `target` 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

**示例 1：**

```
输入：target = 9
输出：[[2,3,4],[4,5]]
```

**示例 2：**

```
输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```

**限制：**

*   `1 <= target <= 10^5`

#### Solution

Language: ****

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        if (target <=2) {
            return new int[0][0];
        }
        List<List<Integer>> res = new ArrayList<>();
        int left = 1;
        int right = 1;
        int n = target/2+1;
        List<Integer> tmp = new ArrayList<>();
        int cur = 0;
        while(right <= n) {
            cur += right;
            tmp.add(right);
            while (cur >= target) {
                if (cur == target) {
                    res.add(new ArrayList<>(tmp));
                } 
                tmp.remove(0);
                cur -= left;
                left += 1;
            }
            right += 1;
        }
        return convert(res, n);
    }

    private int[][] convert(List<List<Integer>> res, int n) {
        int[][] ans = new int[res.size()][];
        int idx = 0;
        for(List<Integer> list : res) {
            ans[idx] = new int[list.size()];
            int j = 0;
            for(int x : list) {
                ans[idx][j++] = x;
            }
            idx += 1;
        }
        return ans;
    }
}
```



下面这张写法更加优雅一些，而且效率更高

```java
class Solution {
    public int[][] findContinuousSequence(int target) {
        List<int[]> res = new ArrayList<>();
        int left = 1;
        int right = 1;
        int n = target/2+1;
        int cur = 0;
        while(right <= n) {
            cur += right;
            while (cur > target) {
                cur -= left++;
            }
            if (cur == target) {
                int[] tmp = new int[right-left+1];
                for(int k=0;k<right-left+1;k++) {
                    tmp[k] = left+k;
                }
                res.add(tmp);
            }
            right += 1;
        }
        int[][] ans = new int[res.size()][];
        for(int i=0;i<res.size();i++) {
            ans[i] = res.get(i);
        }
        return ans;
    }
}
```

