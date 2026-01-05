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
  - [codings](#codings-4)

> 梦开始的地方

* [leetcode 梦开始的编程之旅](https://leetcode.cn/studyplan/primers-list/)
* 2026/01/05 进度 5/18，在 [1486. 数组异或操作](#1486-数组异或操作)


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
