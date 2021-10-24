### [剑指 Offer 16\. 数值的整数次方](https://leetcode-cn.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

Difficulty: **中等**


实现  ，即计算 x 的 n 次幂函数（即，x<sup>n</sup>）。不得使用库函数，同时不需要考虑大数问题。

**示例 1：**

```
输入：x = 2.00000, n = 10
输出：1024.00000
```

**示例 2：**

```
输入：x = 2.10000, n = 3
输出：9.26100
```

**示例 3：**

```
输入：x = 2.00000, n = -2
输出：0.25000
解释：2-2 = 1/22 = 1/4 = 0.25
```

**提示：**

*   `-100.0 < x < 100.0`
*   `-2<sup>31</sup> <= n <= 2<sup>31</sup>-1`
*   `-10<sup>4</sup> <= x<sup>n</sup> <= 10<sup>4</sup>`

注意：本题与主站 50 题相同：


#### Solution

Language: ****



方法1，使用了递归，没有使用二分法考虑，而且还存在**1.00000 -2147483648** 这个测试数据，贸然处理肯定会出错，改成long才通过了

```java
class Solution {
    public double myPow(double x, int n) {
        return pow(x, n);
    }

    private double pow(double x, long n) {
        if (n < 0) {
            return 1.0 / pow(x, -n);
        } else if (n == 0) {
            return 1.0;
        } else if (n == 1) {
            return x;
        }
        double tmp = pow(x, n/2);
        if (n % 2 == 0) {
            return tmp * tmp;
        }
        return tmp * tmp * x;
    }
}
```



方法二，采用二分法