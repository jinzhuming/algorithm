>在计算机科学中，二分搜索（英语：binary search），也称折半搜索（英语：half-interval search）[1]、对数搜索（英语：logarithmic search）[2]，是一种在有序数组中查找某一特定元素的搜索算法。搜索过程从数组的中间元素开始，如果中间元素正好是要查找的元素，则搜索过程结束；如果某一特定元素大于或者小于中间元素，则在数组大于或小于中间元素的那一半中查找，而且跟开始一样从中间元素开始比较。如果在某一步骤数组为空，则代表找不到。这种搜索算法每一次比较都使搜索范围缩小一半。

二分查找法主要是解决在 ***“一堆数中找出指定的数”*** 这类问题。

而想要应用二分查找法，这“一堆数”必须有一下特征：

 1. 存储在数组中
 2. 有序排列

所以如果是用**链表存储**的，就无法在其上应用二分查找法了。

至于是顺序递增排列还是递减排列，数组中是否存在相同的元素都不要紧。不过一般情况，我们还是希望并假设数组是递增排列，数组中的元素互不相同。

**复杂度分析**

[时间复杂度](https://zh.wikipedia.org/wiki/%E6%97%B6%E9%97%B4%E5%A4%8D%E6%9D%82%E5%BA%A6)

折半搜索每次把搜索区域减少一半，时间复杂度为O(logn)。

[空间复杂度](https://zh.wikipedia.org/wiki/%E8%A8%88%E7%AE%97%E8%A4%87%E9%9B%9C%E6%80%A7%E7%90%86%E8%AB%96)

O(log1)虽以递归形式定义，但是尾递归，可改写为循环。

**步骤**

给予一个包含n个带值元素的数组A或是记录A0 ... An−1，使得A0 ≤ An−1，以及目标值T，还有下列用来搜索T在A中位置的子程序。

令L为0，R为n− 1。

如果L > R，则搜索以失败告终。

令m（中间值元素）为“(L + R) / 2”加上下高斯符号。

如果Am < T，令L为m + 1并回到步骤二。

如果Am > T，令R为m - 1并回到步骤二。

当Am = T，搜索结束；回传值m。

这个迭代步骤会持续通过两个变量追踪搜索的边界。有些实际应用会在算法的
最后放入相等比较，让比较循环更快，但平均而言会多一层迭代[4]。

```
const a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]

// 给 Array 添加二分查找方法
  Array.prototype.binarySearch = function(low, high, khey) {
    if (low > high) {
      return -1
    }

    const mid = parseInt((high + low) / 2)

    if (this[mid] > khey) { 
      return this.binarySearch(low, mid - 1, khey)
    }

    if (this[mid] < khey) {
      return this.binarySearch(mid + 1, high, khey)
    }
    
    return mid
  }

  a.binarySearch(0, a.length - 1, 9) // 8
```
详细代码地址为 [冒泡排序](https://github.com/jinzhuming/Algorithm/blob/master/binarySearch/index.html/)