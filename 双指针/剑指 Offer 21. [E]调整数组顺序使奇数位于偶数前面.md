### [剑指 Offer 21\. 调整数组顺序使奇数位于偶数前面](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

Difficulty: **简单**


输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位于数组的后半部分。

**示例：**

```
输入：nums = [1,2,3,4]
输出：[1,3,2,4] 
注：[3,1,2,4] 也是正确的答案之一。
```

**提示：**

1.  `0 <= nums.length <= 50000`
2.  `0 <= nums[i] <= 10000`


#### Solution

Language: ****

```java
class Solution {
    public int[] exchange(int[] nums) {
        // 奇数在前面，偶数在后面
        int left = 0, right = nums.length-1;
        while(left < right) {
            while(left < right && nums[left] % 2 == 1) {
                left += 1;
            }
            while(left < right && nums[right] % 2 == 0) {
                right -= 1;
            }
            if (left < right) {
                swap(nums, left++, right--);
            }
        }
        return nums;
    }

    private void swap(int[] nums, int i, int j) {
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
}
```