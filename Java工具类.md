# Java常用工具

## 1.异常

```java
public class Main {
    public void main(String[] args) {
        try{
            ...
        } catch ( Exception1 | Exception2 e) {
            System.out.println(e);
        } finally {
            ...
        }
    }
}
```

- 对于异常, 可以使用`e.printStackTrace()`方法打印异常栈;

## 2.包装类

- 为了是操作更有效率, 给每一种基本类型提供了包装类;
- 装箱, 拆箱
  - 装箱: 从基本类型转换为对应的包装类型对象, `Integer i = 100;`
  - 拆箱: 从包装类对象转换为对应的基本类型; `int index = i`;
- 自动装箱: 可以使用`Integer i = 100`直接创建包装类对象, 而不使用`new`;

![包装类](./image/包装类.jpg)

## 3.集合

## 4.多线程

### 1.线程创建

> `Thread`: 通过`start()`启动线程, 线程执行`run()`方法;
>
> `Runable`: 用于实现线程的接口, 只有一个`run()`方法;

- 继承`Thread`类, 重写`run()`方法;

```java
class Mythread extends Thread{
    public void run() {
        System.out.println("执行线程");
    }
}
```

- 实例化`Thread`的时候传入一个`Runable`的实例;

```java
public class Main {
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable());
        t.start();
    }
}

class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("执行线程!");
    }
}
```

### 2.线程同步

- `synchronized`: 关键字, 用于对一个对象进行加锁.

```java
synchronized(lock) {
    n = n + 1;
}
```

- 用`synchronized`修饰方法可以把整个方法变为同步代码块, 相当于对`this`进行加锁;

```java
public synchronized void add(int n) {
    count += n;
}

/* 相当于 */

public void add(int n) {
    synchronized(this){
        count += n;
    }
}
```

- `synchronized`的关键就是锁住的对象;
