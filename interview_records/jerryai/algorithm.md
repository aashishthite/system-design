
# 算法1
## 描述
题目是给一串数字（0 - 9）每个数字之间可以加 + - 号或者不加，组成的表达式计算结果等于 给定的目标数，输出所有满足条件的表达式。
例如： [1 2 3 4 5 6 7 8 9]  目标 100
可能的组合：
1 + 23 - 4 + 56 + 7 + 8 + 9
-1 - 2 + 34 - 5 - 6 + 78 + 9

## 链接
* https://www.1point3acres.com/bbs/thread-859737-1-1.html

# 算法2
## 描述
应该算是一道easy-medium，给定一个数组，只有一个初始数字1，对这个数组的每个数字k，做k*2+1和k*3+1，然后加入数组，要求这个数组是sorted并且没有重复元素，返回第N个
这个数组应该是[1,3,4,7,9,10,13,....]
算法
3(1*2+1), 4(1*3+1)
7(3*2+1), 10(3*3+1)
9(4*2+1), 13(4*3+1)

## 解法分析
因为出现了3算出来的比4还大，所以单纯用queue不行，要用heap，然后用set去重

这个题需要处理的点是对于两个相邻的elements - a(k) 和 a(k+1)，a(k) * 3 + 1 有可能大于 a(k+1) * 2 + 1，所以要排序。
解法一：用一个heap，每次从里面拿最小值。复杂度 O(n logn)
解法二：观察到 k*2 + 1 和 k*3 + 1两个数组是独立递增的，所以可以维护两个deque，每次从两个deque的头去最小值，然后把新的element放到相应的队列里。复杂度 O(n)
我给出的是第二个解法，这轮pass

## 链接
https://www.1point3acres.com/bbs/thread-900233-1-1.html

# 算法3
## 描述
coding只有15分钟到20分钟，题目是给一个int，输出最小的，大于这个数的回文串：比如说：12300 -> 12321。

## 分析
解答：分情况讨论，基本思路是从中间劈开，‍‍‍‍‌‌‌‍‍‍‌‍‍‌‍‍‌‍构建回文串，如果需要在中间+1的话就+1，比如12385 -> 12421。但是这个有好多edge case，比如999，个位数一类的，我没有cover所有的edge case

# 算法4
## 描述
implement lru
力扣易思柳，LRU题，之前没刷过，想到了用Dictionary和linkedlist来处理. 可以通过linkedlistnode 的prev和next快速定位来删除node，做到O(1) put和get

# 算法5
## 描述
// 给定两个整数，被除数 dividend 和除数 divisor。将两数相除，要求不使用乘法、除法和 mod 运算符。
// 返回被除数 dividend 除以除数 divisor 得到的商。
// 整数除法的结果应当截去（truncate）其小数部分，例如：truncate(8.345) = 8 以及 truncate(-2.7335) = -2
// 输入: dividend = 10, divisor = 3
// 输出: 3
// 解释: 10/3 = truncate(3.33333..) = truncate(3) = 3

# 算法6
## 描述
// 整数数组 nums 按升序排列，数组中的值 互不相同 。
// 在传递给函数之前，nums 在预先未知的某个下标 k（0 <= k < nums.length）上进行了 旋转，使数组变为 [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]（下标 从 0 开始 计数）。例如， [0,1,2,4,5,6,7] 在下标 3 处经旋转后可能变为 [4,5,6,7,0,1,2] 。
// 给你 旋转后 的数组 nums 和一个整数 target ，如果 nums 中存在这个目标值 target ，则返回它的下标，否则返回 -1 。
// 示例：
// 输入：nums = [4,5,6,7,0,1,2], target = 0
// 输出：4
