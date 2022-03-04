## 知识点

1.8版本取消了1.7中的分段锁策略，使用了`CAS + synchronized`来保证安全性。

## 参考

#### [啃碎JDK源码(五)：ConcurrentHashMap](https://segmentfault.com/a/1190000022279729)



## 面试题

1. 为什么ConcurrentHashMap是线程安全的

