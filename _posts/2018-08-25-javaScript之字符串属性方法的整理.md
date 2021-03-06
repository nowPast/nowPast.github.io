

























































































































































































































































































































































































# javaScript之字符串属性方法的整理

> ## 绝知此事需手书

1. 字符串属性

- String.length
  - 描述：表示字符串的字符长度；

2. 字符相关的方法

- charAt(index)
  - 描述：接收一个表示字符位置的索引参数，获取/访问指定索引位置的字符；
  - 也可以使用方括号加索引的方式实现相同的结果：string[index]；

- charCodeAt(index)

  - 描述：获取/访问指定索引位置的字符的ASCII编码；

- 注意：

  当传入的参数超出实际字符串的index范围后，则返回空字符串（表现为不返回任何值，但也不报错）；

  字符串指定位置中如果有空格，则返回空字符串（表现为不返回任何值，但也不报错）；

3. 字符串的操作方法（**以下4个方法都不会修改原来的字符串**）

- concat()

  - 描述：用于连接字符串；一般不用，在字符串时最常使用：**+**；

- 三个基于子字符串创建新字符串的方法：slice() substr() substring()

  - 都接收一个或两个参数；
  - 第一个参数表示，指定子字符串开始的位置；
  - 当只有一个参数时，解释器执行时会默认补充上第二个参数，参数值为原字符串的length（或者可以直接理解为，当这三个方法只传入了一个参数时，表示从该参数的索引位置一直截取到原字符串的结束位置）；

- slice()

  - slice()与substring()的第二个参数，指截取的子字符串结束在以该参数为索引的字符之前；

  - 当传入的参数为负值时；slice会将负值参数与原字符串的长度相加；

  - **slice截取规则总结：**

    - 如果只有一个参数时，则补充第二个参数，参数值为原字符串的length值；

    - 如果参数中有负值，无论负值出现在第一个参数还是第二个参数的位置，则将负值与原字符串的长度相加；

    - 对于经过上述规则的转换后，**在正式截取运算前，slice的参数最终都需要转换为符合截取运算逻辑的两个都大于或等于0的值**，然后按照**第一个参数为截取子字符串的开始位置，第二个参数为子字符串结束在该索引字符之前进行截取**；

    - 如果在经过上述的转换规则后，参数仍然不符合截取的运算规则时，则返回空字符串（看起来不会返回任何结果，但也不会报错）；

    - eg：当只有一个参数且为负值时：

      ![](https://github.com/nowpast/md-imgs/raw/master/-slice1.png)

    - eg：当有两个参数时，且第一个参数为正数，第二个参数为负值时：

      运行时，会将传入的第二个负值的参数与字符串的长度相加，然后在按照正常的两个正值参数进行截取；
      ![](https://github.com/nowpast/md-imgs/raw/master/-slice2.png)

- substring()

  - slice()与substring()的第二个参数，指截取的子字符串结束在以该参数为索引的字符之前；

  - 当传入的参数为负值时；substring会将负值参数转为0；

  - **substring截取规则总结：**

    - 如果只有一个参数时，则补充第二个参数，参数值为原字符串的length值；
    - 如果参数中有负值，无论负值出现在第一个参数还是第二个参数的位置，都会将负值参数转换为0；
    - 对于经过上述规则的转换后，**在正式截取运算前，substring的参数最终都需要转换为符合截取运算逻辑的两个都大于或等于0的值**，然后按照**第一个参数为截取子字符串的开始位置，第二个参数为子字符串结束在该索引字符之前进行截取**；
    - 如果在经过上述的转换规则后，参数仍然不符合截取的运算规则时，则返回空字符串（看起来不会返回任何结果，但也不会报错）；

    - 当只有一个参数且为负值时：

      第一步补充第二个参数；第二步将负值转为0；最终都相当于从第一个字符一直截取到结尾，即复制了原字符串；

      ![](https://github.com/nowpast/md-imgs/raw/master/substring0.png)

    - 当有两个参数，第一个参数为正值，第二个参数为0，属于不符合截取运算的一种，但substring对此有一个特殊的截取规则：

      运行时，会返回从首位开始截取，个数为第一个参数的值的子字符串；

      ![](https://github.com/nowpast/md-imgs/raw/master/substring1.png)

    - eg：当有两个参数时，且第一个参数为正值，第二个参数为负值时：

      运行时，substring方法会把负值参数转换为0，这种情况下参考上一个情况，会返回从首位开始截取，个数为第一个参数的值的子字符串；

      ![](https://github.com/nowpast/md-imgs/raw/master/substring3.png)

    - eg：当有两个参数时，且第一个参数为负值时，第二个参数为正值时

      运行时，substring，会把负值参数转换为0，会返回从首位开始截取，一直截取到第二个参数为索引之前的位置；

      ![](https://github.com/nowpast/md-imgs/raw/master/substring4.png)

    - **除此之外，所有其他传入不符合截取字符串运算逻辑的参数时，都不会返回任何结果，当也不会报错；**

- substr()

  - substr()的第二个参数指截取的子字符串的字符个数；

  - 当传入的参数为负值时；

    在执行时，substr会把第一个负值参数与原字符串的长度相加；把第二个负值参数转换为0；经过转换后再根据**第一个参数表示截取子字符串的开始位置，第二个参数表示截取子字符串的字符个数**进行截取；

  - **substr()截取规则总结**

    - 第一步：如果只有一个参数时，则补充第二个参数，参数值为原字符串的length值；
    - 第二步：参数中有负值时，则把第一个负值参数与原字符串的长度相加；把第二个负值参数转换为0（代表截取0个字符，也就是说只有第二个参数为负值就不会有任何返回结果）；
    - 第三步：结果转换后，按照**第一个参数表示截取子字符串的开始位置，第二个参数表示截取子字符串的字符个数**进行截取；**当第二个参数超过可截取的个数时，则从第一个参数的位置开始截取直到原字符串结尾（即能截取的多少就截取多少）**；如果转换后的参数仍然不符合截取的运算规则时，则返回空字符串（看起来不会返回任何结果，但也不会报错）；

4. 有关字符串位置的方法

   作用：用于在字符串中搜索给定字符的索引位置，找到后返回字符串的索引，没有找到这返回‘-1’；

   传入一个或两个参数，第一个参数为要搜索的字符，第二个参数为搜索的起始位置；

- indexOf()

  从头到尾，正序先后搜索；

- lastIndexOf()

  从尾到头，倒序向前搜索；

5. trim()

- 创建一个字符串的副本，删除前置和后缀的所有空格然后返回结果，不会对原字符串做任何修改；
- ES5才新增的trim方法，IE9+才支持；

6. 大小写转换

- toLowerCase()

- toLocalLowerCase()

  针对当地地区实现大小写转换

- toUpperCase()

- toLocalUpperCase()

  针对当地地区实现大小写转换

- 注意：在不知道代码在哪种语言环境下运行的时候，建议使用针对当地地区的方法跟稳妥；

7. 模式匹配方法

- match()

  - 只接收一个参数：要检索的字符串或者正则表达式/RegExp对象；

  - 返回值：

    - 一个或多个满足参数条件的元素构成的数组；

    - 到底是一个数组的元素，还是多个数组元素，依赖于正则表达式参数中是否具有全局标志 g。

    - 如果没有全局标志则找到第一个满足的子字符串就返回给结果数组，不再检索剩余字符；

    - 如果由全局标志g，则会对原字符串从头至尾进行全局检索，检索出所有满足参数条件的子字符串；

    - 对于返回值只有一个元素的情况：该数组的第 0 个元素存放的是匹配文本；此外还有三个对象index（匹配文本的起始字符在原字符串中的索引位置）；input（对原字符串的引用）；groups（存放着与正则表达式的子表达式匹配的文本）

      ![](https://github.com/nowpast/md-imgs/raw/master/match.png)

      ![](https://github.com/nowpast/md-imgs/raw/master/macth1-1.png)

    - 对于实行全局检索，结果由多个元素的情况，返回结果是正常的只满足正则条件的子字符串，并无其他多余属性；

      ![](https://github.com/nowpast/md-imgs/raw/master/match2.png)

      ![](https://github.com/nowpast/md-imgs/raw/master/match2-2.png)

  - 如果没有找到满足的匹配项，则返回null；

- search()

  - 于match参数一样，只接收一个参数：要检索的字符串或者正则表达式/RegExp对象；
  - 返回值
    - 第一个与 regexp参数 相匹配的子字符串的首位字符的索引位置
  - 如果没有找到任何匹配的子串，则返回 -1；

- replace()

  - 用法：用于检索出匹配的字符串并替换；

  - 参数

    - 两个参数：第一个参数为要检索的字符串或正则；第二个参数为替换的内容；

  - 返回

    返回一个检索出满足的子字符并替换了的新的字符串；

  - 同样，如何正则有全局标志g，则检索出全部匹配的子字符串并替换，没有全局标志g，则只替换第一个满足条件的；

- split()

  - 作用：用于将字符串匹配到参数删除；任何后从删除处割裂，成独立的元素；组成一个数组
  - 参数：跟以上相同可以为字符（串）或者正则；
    - 如果不传参数则，返回一个将原字符串作为一个元素的数组；
    - 如果传入空字符串 ("") ，则原字符串中每个字符之间都会被分割，然后构成一个数组；

8. localCompare()todo
9. fromCharCode()todo


---