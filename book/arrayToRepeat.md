> 数组去重(数组重复检查)是一个前端常用到的算法，有很多种方法，这里简单列出几种常用的方法。

**如果只是简单的数组可以通过 遍历数组、indexOf、set 等方法去重**

> 遍历数组

```
const newArr = []
for (let value of arr) {
  let state = false
  for (let newArrVal of newArr) {
    if (value === newArrVal) {
      // 重复
      state = true
      break
    }
  }
  if (!state) {
    newArr.push(value)
  }
}
return newArr
```
1. 构建一个新的数组。
2. 遍历一遍当前数组。
3. 遍历新数组。
4. 用当前数组中的每一个值和旧数组对比，发现重复则丢弃，否则插入新数组。
5. 遍历完成，返回新数组，即去重。

这种方法因为效率低下，所以最好不要采用

> indexOf
indexOf()方法返回在数组中可以找到给定元素的第一个索引，如果不存在，则返回-1

```
const newArr = []
for (let value of arr) {
  if (newArr.indexOf(value) < 0) {
    newArr.push(value)
  }
}
return newArr
```

1. 简历新的数组。
2. 遍历当前数组。
3. 利用 indexOf 判断新数组内是否有当前元素，发现重复则丢弃，否则插入新数组
4. 遍历完成，返回新数组，即去重。

相对于遍历两次，使用 indexOf 更加简单

> set Array.from
Array.from() 是 es6 新增方法，用于将对象转化为真正的数组
Set 用来生成一个新的数据结构，他的元素都是非重复的

```
return Array.from(new Set(arr))

```
1. 将对象转化为真正的数组
2. 使用 Set 转化为没有重复的新结构
-----

详细代码地址为 [数组去重](https://github.com/jinzhuming/algorithm/blob/master/arrayToRepeat/index.html)
