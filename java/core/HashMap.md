## 知识点

##### 底层原理: 

​	数据结构是 数组+链表,链表会在长度大于8时变为红黑树

##### 扩容机制: 

​	数据量>=总容量*加载因子(默认0.75)时会进行扩容,容量翻倍

##### 加载因子: 

​	为什么默认是0.75, 太小的话容易浪费空间, 太大的话容易hash冲突, 浪费时间, 折中

##### 红黑树: 

​	自平衡树二叉树, 从根到叶子最长的路径不大于最短路径的两倍;可以防止查询时间差距过大, 又不像完全平衡二叉树在平衡上有较大的消耗



## 参考

#### [Java 8系列之重新认识HashMap](https://tech.meituan.com/2016/06/24/java-hashmap.html)



## 面试题

1. hashmap的底层结构
2. hashmap如何扩容
3. hashmap为什么用红黑树, 为什么不用B+树

