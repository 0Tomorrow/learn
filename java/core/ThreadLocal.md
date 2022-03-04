## 知识点

**ThreadLocal的作用主要是做数据隔离，填充的数据只属于当前线程，变量的数据对别的线程而言是相对隔离的，在多线程环境下，防止自己的变量被其它线程篡改。**

- #### 实现

  **存储:**

  ```java
      public void set(T value) {
          Thread t = Thread.currentThread();
          ThreadLocalMap map = getMap(t); // 获取线程的ThreadLocalMap
          if (map != null)
              map.set(this, value); // 将数据放到ThreadLocalMap中
          else
              createMap(t, value);
      }
  ```

  **查询:**

  ```java
      public T get() {
          Thread t = Thread.currentThread();
          ThreadLocalMap map = getMap(t); // 获取线程的ThreadLocalMap
          if (map != null) {
              // 从ThreadLocalMap中获取value, key是当前的ThreadLocal对象
              ThreadLocalMap.Entry e = map.getEntry(this); 
              if (e != null) {
                  @SuppressWarnings("unchecked")
                  T result = (T)e.value;
                  return result;
              }
          }
          return setInitialValue();
      }
  ```

  

- #### 如何做到隔离的

  **数据是存到当前线程对象Thread中的, Thead中用属性ThreadLocal.ThreadLocalMap来存储数据, 所以只有当前线程能拿到数据, 做到隔离;**

- #### ThreadLocal.ThreadLocalMap

  **数据结构是KV列表, 类似map结构, 但是没有实现map接口;**

  **key是ThreadLocal对象, value是存储的值**

  **存储时使用KEY的hash来定位位置, 如果发生了冲突, 则定位到该位置的后一位, 如果继续冲突, 则继续往后, 直到不冲突; 查询类似;**



## 参考

#### [Java面试必问：ThreadLocal终极篇 淦！](https://www.cnblogs.com/aobing/p/13382184.html)



## 面试题

