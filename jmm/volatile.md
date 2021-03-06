## 知识点

### 特性:

- **保证可见性，不保证原子性**

  a.当写一个volatile变量时，JMM会把该线程本地内存中的变量强制刷新到主内存中去；

  b.这个写会操作会导致其他线程中的缓存无效。

- **禁止指令重排**

### 适用场景:

对于普通的共享变量来讲，线程A将其修改为某个值发生在线程A的本地内存中，此时还未同步到主内存中去；而线程B已经缓存了该变量的旧值，所以就导致了共享变量值的不一致。解决这种共享变量在多线程模型中的不可见性问题，较粗暴的方式自然就是加锁，但是此处使用synchronized或者Lock这些方式太重量级了，比较合理的方式其实就是volatile。



## 参考

#### [Java中volatile关键字的最全总结](https://cloud.tencent.com/developer/article/1618122)



## 面试题

1. volatile有什么用, 能不能保证原子性