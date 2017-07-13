> **希尔排序（英语：Shellsort）**，希尔排序，也称递减增量排序算法，是插入排序的一种更高效的改进版本。希尔排序是非稳定排序算法。

希尔排序是基于插入排序的以下两点性质而提出改进方法的：
* 插入排序在对几乎已经排好序的数据操作时，效率高，即可以达到线性排序的效率
* 但插入排序一般来说是低效的，因为插入排序每次只能将数据移动一位

**历史**

希尔排序按其设计者希尔（Donald Shell）的名字命名，该算法由1959年公布。一些老版本教科书和参考手册把该算法命名为Shell-Metzner，即包含Marlene Metzner Norton的名字，但是根据Metzner本人的说法，“我没有为这种算法做任何事，我的名字不应该出现在算法的名字中。”

**算法实现**

希尔排序是基于插入排序的以下两点性质而提出改进方法的：
插入排序在对几乎已经排好序的数据操作时， 效率高， 即可以达到线性排序的效率
但插入排序一般来说是低效的， 因为插入排序每次只能将数据移动一位
算法思路：
1. 先取一个正整数 d1(d1 < n)，把全部记录分成 d1 个组，所有距离为 d1 的倍数的记录看成一组，然后在各组内进行插入排序
2. 然后取 d2(d2 < d1)
3. 重复上述分组和排序操作；直到取 di = 1(i >= 1) 位置，即所有记录成为一个组，最后对这个组进行插入排序。一般选 d1 约为 n/2，d2 为 d1 /2， d3 为 d2/2 ，…， di = 1。

例如：
数组 [9, 1, 0, 8, 7 ,5，2]
取 d1 = 3
分为 3组
* 9, 8, 2 
* 1, 7
* 0, 5
分别对其进行排序，得到结果
[2, 1, 0, 8, 7, 5, 9]

取 d2 = 2
分为 2 组
* 2, 0, 7, 9
* 1, 8, 5
再次排序，得到
[0, 1, 2, 5, 7, 8, 9]

d3 = 1
进行一次插入排序
得到结果
[0, 1, 2, 5, 7, 8, 9]


**相关**
[插入排序](https://github.com/jinzhuming/algorithm/blob/master/book/insertionSort.md)

代码实现
```
  let a = [1, 3, 0, 5, 4, 2]

  Array.prototype.shellSort = function() {
    function swap(array, i, k) {
        var temp = array[i];
        array[i] = array[k];
        array[k] = temp;
    }

    var length = this.length,
        gap = Math.floor(length / 2);
    while (gap > 0) {
        for (var i = gap; i < length; i++) {
            for (var j = i; 0 < j; j -= gap) {
                if (this[j - gap] > this[j]) {
                    swap(this, j - gap, j);
                } else {
                    break;
                }
            }
        }
        gap = Math.floor(gap / 2);
    }

    return this
  }

  a = a.shellSort()
```
详细代码地址为 [希尔排序](https://github.com/jinzhuming/Algorithm/blob/master/shellSort/index.html/)

