# javaScript之数组属性方法的整理

##  属性

### length属性

- 利用length属性可以方便地在数组末尾添加新项；

  由于数组最后一项的索引始终是length-1，因此下一个新项的位置就是length；

## 方法

### 检测数组

- ES5新增了Array.isArray()，用于确定某个值是不是数组；


  ```
  		var arr = [1,2,3];
  		var result = Array.isArray(arr);  // √
  		var result = arr.isArray();       // ×
  ```

### 栈方法

- 栈后进先出（一个出口）
- push()
- pop()

### 队列方法

- 队列先进先出（两头都通）
- shift---unshift
- push

### 重排序方法

- reverse()
- sort()
  - 小在前，大在后；
  - 为了实现元素间的大小排序，会隐式调用toString();

### 操作方法

- concat
- slice
- splice
  - 语法：`arrayObject.splice(index,howmany,item1,.....,itemX)·`
  - 第一个参数index：代表新增/删除元素的位置，如果是负数表示数组倒数的位置（的前一个位置）开始增删元素；
  - 第二个参数howmany代表要删除的项目数量；如果设置为 0，则不会删除项目；如果省略则不会对原数组产生修改；
  - 第二个之后的元素item，代表向数组中新增的元素；
  - 返回值：返回被删除的元素为数组类型，如果操作没有删除元素，则返回空数组；
  - 请注意，splice() 方法与 slice() 方法的作用是不同的，splice() 方法会直接对数组进行修改。

### 位置方法

- indexOf()
- lastIndexOf()

### 迭代方法

- every()
- filter()
- forEach()
- map()
- some()

### 并归方法

- reduce()
- reduceRight()

### 向字符串转换的方法

- join()

  作用：用于通过指定的分隔符把数组中的所有元素放入一个字符串。

  语法： `arrayObject.join(separator)`

  参数：可选。指定要使用的分隔符。如果省略该参数，则使用**逗号**作为分隔符；如果参数为空字符串‘’，则数组各元素会没有分割的构成一个整体的字符串；



