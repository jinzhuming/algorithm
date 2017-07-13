> **快速排序（英语：Quicksort）**，又称划分交换排序（partition-exchange sort），一种排序算法，最早由东尼·霍尔提出。在平均状况下，排序n个项目要Ο(n log n)次比较。在最坏状况下则需要Ο(n2)次比较，但这种状况并不常见。事实上，快速排序通常明显比其他Ο(n log n)算法更快，因为它的内部循环（inner loop）可以在大部分的架构上很有效率地被实现出来。

快速排序使用分治法（Divide and conquer）策略来把一个序列（list）分为两个子序列（sub-lists）。

**步骤为：**

从数列中挑出一个元素，称为"基准"（pivot），
重新排序数列，所有比基准值小的元素摆放在基准前面，所有比基准值大的元素摆在基准后面（相同的数可以到任一边）。在这个分区结束之后，该基准就处于数列的中间位置。这个称为分区（partition）操作。
递归地（recursively）把小于基准值元素的子数列和大于基准值元素的子数列排序。
递归到最底部时，数列的大小是零或一，也就是已经排序好了。这个算法一定会结束，因为在每次的迭代（iteration）中，它至少会把一个元素摆到它最后的位置去。

**优化的排序算法**

快速排序是二叉查找树（二叉查找树）的一个空间最优化版本。不是循序地把数据项插入到一个明确的树中，而是由快速排序组织这些数据项到一个由递归调用所隐含的树中。这两个算法完全地产生相同的比较次数，但是顺序不同。对于排序算法的稳定性指标，原地分区版本的快速排序算法是不稳定的。其他变种是可以通过牺牲性能和空间来维护稳定性的。

快速排序的最直接竞争者是堆排序（Heapsort）。堆排序通常比快速排序稍微慢，但是最坏情况的运行时间总是O(n log n)。快速排序是经常比较快，除了introsort变化版本外，仍然有最坏情况性能的机会。如果事先知道堆排序将会是需要使用的，那么直接地使用堆排序比等待introsort再切换到它还要快。堆排序也拥有重要的特点，仅使用固定额外的空间（堆排序是原地排序），而即使是最佳的快速排序变化版本也需要Θ(log n)的空间。然而，堆排序需要有效率的随机存取才能变成可行。

快速排序也与归并排序（Mergesort）竞争，这是另外一种递归排序算法，但有坏情况O(n log n)运行时间的优势。不像快速排序或堆排序，归并排序是一个稳定排序，且可以轻易地被采用在链表（linked list）和存储在慢速访问媒体上像是磁盘存储或网络连接存储的非常巨大数列。尽管快速排序可以被重新改写使用在炼串列上，但是它通常会因为无法随机存取而导致差的基准选择。归并排序的主要缺点，是在最佳情况下需要Ω(n)额外的空间。

**复杂度**

1. 平均复杂度
![image](https://wikimedia.org/api/rest_v1/media/math/render/svg/080cf0926b920274d591f53311ea7f0278daf5b4)

2. 空间复杂度

最好
![image](https://wikimedia.org/api/rest_v1/media/math/render/svg/1aa93d525926a7551c9f8b92cfbb4d900f053eb8)

最坏
![image](https://wikimedia.org/api/rest_v1/media/math/render/svg/a136b5989c45f9d566e1e7d4e614a96337e20dbb)

代码实现
```
  let a = [1, 3, 0, 5, 4, 2]

  Array.prototype.quickSort = function() {
    var len = this.length

    if (len <= 1) {
      return this.slice(0)
    }

    const left = []
    const right = []
    const mid = this.splice(0, 1)

    for (let key of this) {
      if (key < mid[0]) {
        left.push(key)
      }
      if (key >= mid[0]) {
        right.push(key)
      }
    }

    return left.quickSort().concat(mid.concat(right.quickSort()))
  }

  a = a.quickSort()
```

详细代码地址为 [冒泡排序](https://github.com/jinzhuming/Algorithm/blob/master/quickSort/index.html/)
