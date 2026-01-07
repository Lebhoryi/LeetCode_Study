- [总结](#总结)
- [2235. 两整数相加](#2235-两整数相加)
  - [codings](#codings)
- [2469. 温度转换](#2469-温度转换)
  - [codings](#codings-1)
- [2413. 最小偶倍数](#2413-最小偶倍数)
  - [方案](#方案)
  - [codings](#codings-2)
- [2236. 判断根结点是否等于子结点之和](#2236-判断根结点是否等于子结点之和)
  - [codings](#codings-3)
- [1486. 数组异或操作](#1486-数组异或操作)
  - [天才位运算](#天才位运算)
  - [codings](#codings-4)
- [1512. 好数对的数目](#1512-好数对的数目)
  - [方案一 暴力枚举 O(n^2)](#方案一-暴力枚举-on2)
  - [方案二 哈希表 O(n)](#方案二-哈希表-on)
- [709. 转换成小写字母](#709-转换成小写字母)
  - [codings](#codings-5)
- [258. 各位相加](#258-各位相加)
  - [codings](#codings-6)
- [1281. 整数的各位积和之差](#1281-整数的各位积和之差)
  - [codings](#codings-7)

> 梦开始的地方

* [leetcode 梦开始的编程之旅](https://leetcode.cn/studyplan/primers-list/)
* 2026/01/05 进度 5/18，在 [1486. 数组异或操作](#1486-数组异或操作)
* 2026/01/07 进度 5/18，在 [1486. 数组异或操作](#1486-数组异或操作)，学习天才位运算
* 2026/01/07 进度 10/18，[258. 各位数求和简直神了。](#258-各位相加)

# 总结

1. 经典判断奇数偶数：位运算， `n & 1`， 0 为偶数，1 为奇数。（大数友好）
2. 左移运算符 `<<` 可以将一个数的二进制位向左移动指定的位数，相当于乘以 2 的幂。 例如，`n << 1` 相当于 `n * 2`。

# 2235. 两整数相加

> [2235. 两整数相加](https://leetcode.cn/problems/add-two-integers/)
> 
> 简单
> 
> @date 2026-01-05 22:38

## codings

* python
```python
class Solution:
    def sum(self, num1: int, num2: int) -> int:
        return num1 + num2
```

* cpp
```cpp
class Solution {
public:
    int sum(int num1, int num2) {
        return num1 + num2;
    }
};
```

---

# 2469. 温度转换
> [2469. 温度转换](https://leetcode.cn/problems/convert-the-temperature/)
> 
> 简单
> 
> @date 2026-01-05 23:07

## codings

* python:
```python
class Solution:
    def convertTemperature(self, celsius: float) -> List[float]:
        kelvin = celsius + 273.15
        fahrenheit = celsius * 1.80 + 32.00
        return [kelvin, fahrenheit]
```

* cpp:
```cpp
class Solution {
public:
    vector<double> convertTemperature(double celsius) {
        double kelvin = celsius + 273.15;
        double fahrenheit = celsius * 1.80 + 32.00;
        return {kelvin, fahrenheit};
        // 灵神, 直接返回
        // return {celsius + 273.15, celsius * 1.80 + 32.00};
    }
};
```

---

# 2413. 最小偶倍数
> [2413. 最小偶倍数](https://leetcode.cn/problems/smallest-even-multiple/)
> 
> 简单
> 
> @date 2026-01-05 23:20

## 方案
* 方案一：if else
* 方案二：取余 + 乘法
* 方案三：取余 + 位运算

## codings

* python
```python
class Solution:
    def smallestEvenMultiple(self, n: int) -> int:
        return n if n % 2 == 0 else n * 2
```

* cpp
```cpp
class Solution {
public:
    int smallestEvenMultiple(int n) {
        // return (n % 2 == 0) ? n : (n * 2);
        // return (n % 2 + 1) * n;
        return n << (n & 1);
    }
};
```
---
# 2236. 判断根结点是否等于子结点之和
> [2236. 判断根结点是否等于子结点之和](https://leetcode.cn/problems/root-equals-sum-of-children/)
> 
> 简单
> 
> @date 2026-01-05 23:32

## codings

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def checkTree(self, root: Optional[TreeNode]) -> bool:
        return root.val == root.left.val + root.right.val
```
---
```cpp
class Solution {
public:
    bool checkTree(TreeNode* root) {
        return root->val == root->left->val + root->right->val;
    }
};
```
---
# 1486. 数组异或操作
> [1486. 数组异或操作](https://leetcode.cn/problems/xor-operation-in-an-array/)
> 
> 简单
> 
> @date 2026-01-06 23:42

## 天才位运算

> #灵神 #位运算

给定 start, n, 计算 nums[i] = start + 2*i（下标从 0 开始）且 n == nums.length 。返回 nums 所有元素的异或。

1. start 为偶数，最低位为0，异或结果为0，所有元素右移一位，异或，然后左移一位。不影响结果。$0⊕2⊕4⊕6⊕8=(0⊕1⊕2⊕3⊕4)⋅2=4⋅2=8$
2. start 为奇数。当 n 为偶数时，最低位异或结果为0。当 n 为奇数时，最低位异或结果为1。分成两部分，start + 2*i - 1 同偶数，和 1。
$$
3⊕5⊕7⊕9⊕11=(1⊕2⊕3⊕4⊕5)⋅2+1=1⋅2+1=3
$$
$$
3⊕5⊕7⊕9=(1⊕2⊕3⊕4)⋅2+0=4⋅2+0=8
$$

3. --> 根据1，2，得出公式，a = floor(start/2), b = 1 if n and start is odd else 0, $ret = a⊕(a+1)⊕...⊕(a+n-1)·2+b$

4. $a⊕(a+1)⊕...⊕(a+n-1) = (0⊕1⊕2⊕...⊕(a+n-1))⊕(0⊕1⊕...⊕(a+1))$，因为 $0⊕0=0, 1⊕1=0$，结果转变成了求 0 到 a+n-1 的异或，再异或上 0 到 a+1 的异或.

5. 0 到 n 的异或公式：
$$
\bigoplus_{i=0}^{n} i = 
\begin{cases} 
n, & n = 4k \\
1, & n = 4k + 1 \\
n + 1, & n = 4k + 2 \\
0, & n = 4k + 3 
\end{cases}
$$

6. 代码实现：

```python
class Solution:
    def xorOperation(self, n: int, start: int) -> int:
        xnor_n = lambda n: (n, 1, n+1, 0)[n % 4]
        a = start // 2
        b = n & start & 1
        return (xnor_n(a+n-1) ^ xnor_n(a-1))*2 + b
```

```cpp
class Solution {
    int xnor_n (int n) {
        switch (n % 4) {
            case 0: return n;
            case 1: return 1;
            case 2: return n + 1;
            default: return 0;
        }
    }

public:
    int xorOperation(int n, int start) {
        int a = start / 2;
        int b = n & start & 1;
        return (xnor_n(a + n - 1) ^ xnor_n(a - 1)) * 2 + b;
    }
};
```

## codings

* python
```python
class Solution:
    def xorOperation(self, n: int, start: int) -> int:
        ret = 0
        for i in range(n):
            ret ^= (start + 2*i)
        return ret
```

* cpp
```cpp
class Solution {
public:
    int xorOperation(int n, int start) {
        int ret = 0;
        for (int i = 0; i < n; i++) {
            ret ^= (start + 2*i);
        }
        return ret;
    }
};
```

---

# 1512. 好数对的数目
> [1512. 好数对的数目](https://leetcode.cn/problems/number-of-good-pairs/)
> 
> 简单
> 
> @date 2026-01-07 23:52

## 方案一 暴力枚举 O(n^2)

```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        ret = 0
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] == nums[j]:
                    ret += 1
        return ret
```

## 方案二 哈希表 O(n)
```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        ret = 0
        cnt = defaultdict(int)
        for x in nums:
            ret += cnt[x]
            cnt[x] += 1
        return ret
```
---
```cpp
class Solution {
public:
    int numIdenticalPairs(vector<int>& nums) {
        int ret = 0;
        unordered_map<int, int> cnt;
        for (int x : nums) {
            ret += cnt[x];
            cnt[x]++;
        }
        return ret;
    }
};
```

---

# 709. 转换成小写字母
> [709. 转换成小写字母](https://leetcode.cn/problems/to-lower-case/)
> 
> 简单
> 
> @date 2026-01-07 32:30

## codings
```python
class Solution:
    def toLowerCase(self, s: str) -> str:
        # return s.lower()
        ans = ''
        for ch in s:
            if ord(ch) >= 65 and ord(ch) <= 90:
                ans += chr(ord(ch) | 32)
            else:
                ans += ch
        return ans
```
---
```cpp
class Solution {
public:
    string toLowerCase(string s) {
        for (char& c : s) {
            // if (c >= 'A' && c <= 'Z') {
            //     c = c - 'A' + 'a';
            // }
            if (c >= 65 && c <= 90) {
                c |= 32;
            }
        }
        return s;
    }
};
```
---

# 258. 各位相加
> [258. 各位相加](https://leetcode.cn/problems/add-digits/)
> 
> 简单
> 
> @date 2026-01-07 23:42

## codings

> 灵神，这是一个数学问题。对9取余就是各位相加的结果。

```python
class Solution:
    def addDigits(self, num: int) -> int:
        return (num - 1) % 9 + 1 if num else 0
```
---
```cpp
class Solution {
public:
    int addDigits(int num) {
        return (num - 1) % 9 + 1;
    }
};
```

# 1281. 整数的各位积和之差
> [1281. 整数的各位积和之差](https://leetcode.cn/problems/subtract-the-product-and-sum-of-digits-of-an-integer/)
> 
> 简单
> 
> @date 2026-01-07 23:42

## codings

```python
class Solution:
    def subtractProductAndSum(self, n: int) -> int:
        prod = 1
        sum = 0
        while n:
            prod *= n % 10
            sum += n % 10
            n //= 10
        return prod - sum
```
---
```cpp
class Solution {
public:
    int subtractProductAndSum(int n) {
        int prod = 1;
        int sum = 0;
        while (n) {
            prod *= n % 10;
            sum += n % 10;
            n /= 10;
        }
        return prod - sum;
    }
};
```