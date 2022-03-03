## 知识点

- #### int与Integer的区别

  - Integer是int的包装类；int是基本数据类型；
  
  - Integer变量必须实例化后才能使用；int变量不需要；
  
  - Integer实际是对象的引用，指向此new的Integer对象；int是直接存储数据值 ；
  
  - Integer的默认值是null；int的默认值是0。
  
  - 泛型不支持int，但是支持Integer
  
  - int 存储在栈中，Integer 对象的引用存储在栈空间中，对象的数据存储在堆空间中。
  
    
  
- #### 自动装箱和自动拆箱
  
  自动装箱：将基本数据类型重新转化为对象
  
  ```java
  public class Demo {  
          public static void main(String[] args) {  
              //声明一个Integer对象
              Integer num = 1;
              //以上的声明就是用到了自动的装箱：解析为:Integer num = new Integer(1);
          }  
  }  
  ```
  
  1是属于基本数据类型的，原则上它是不能直接赋值给一个对象Integer的。但jdk1.5后你就可以进行这样的声明，自动将基本数据类型转化为对应的封装类型，成为一个对象以后就可以调用对象所声明的所有的方法。
  
  自动拆箱：将对象重新转化为基本数据类型
  
  ```java
  public class Demo {
      public static void main(String[] args) {
          //自动装箱 将基本数据类型变成对象
          Integer integer = 1;
          //自动拆箱
          System.out.println(integer+10);
      }
  }
  ```
  
  因为对象是不能直接进行运算的，而是要转化为基本数据类型后才能进行加减乘除。
  
  对比：
  
  ```java
  // 装箱
  Integer a = 10;
  // 拆箱
  int b = a;
  复制代码
  ```
  
- #### 相同值下的 int 和 Integer 的比较结果
  
  1. 两个通过new生成的变量，结果为false。

     ```java
     Integer i1 = new Integer(10);
     Integer i2 = new Integer(10);
     System.out.print(i1 == i2); //false
     ```
     
  2. int 和 Integer 的值比较，若两者的值相等，则为true。（注意：在比较时，Integer会自动拆箱为int类型，然后再做比较，实际上就变为两个int变量的比较）
  
     ```java
     Integer i1 = new Integer(10);
     int i2 = 10；
     System.out.print(i1 == i2); //true
     ```
     
  3. new 生成的Integer变量 和 非new 生成的Integer变量比较，结果为false。（注意：new 生成的Integer变量的值在堆空间中，非new 生成的Integer变量的值在在常量池中。非new生成的Integer变量，会先判断常量池中是否有该对象，若有则共享，若无则在常量池中放入该对象；这也叫享元模式）
  
     ```java
     Integer i1 = new Integer(10);
     Integer i2 = 10;
     System.out.print(i1 == i2); //false
     ```
     
  4. 对于两个非new生成的Integer对象，进行比较时，如果两个变量的值在区间-128到127之间，则比较结果为true，如果两个变量的值不在此区间，则比较结果为false。
  
     ```java
     Integer i1 = 10;
     Integer i2 = 10;
     System.out.print(i1 == i2); //true
     Integer j1 = 128;
     Integer j2 = 128;
     System.out.print(j1 == j2); //false
     ```
     
  当值在 -128 ~ 127之间时，java会进行自动装箱，然后会对值进行缓存，如果下次再有相同的值，会直接在缓存中取出使用。缓存是通过Integer的内部类IntegerCache来完成的。当值超出此范围，会在堆中new出一个对象来存储。
  
  

## 参考

#### [int与Integer区别](https://juejin.cn/post/6844903987276169229)



## 面试题

1. int与Integer的区别
2. Integer a = 100; int b = 100; 判断a==b;