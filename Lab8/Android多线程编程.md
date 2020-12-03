# 子线程的程序框架

## 一、实验目的：探究Android的多线程编程

## 二、实验过程：

### 1、主要代码：

#### 框架1

```java
public class MYThread extends Thread{

    @Override
    public void run(){
        //处理具体的逻辑
    }
}
```

#### 框架2

```java
class MYThread implements Runnable{

    @Override
    public void run(){
        //处理具体的逻辑
    }
    
    Mythread mythread = new MYThread();
    new Thread(mythread).start();
}
```

#### 框架3

```java
new Thread(new Runnable(){
    @Override
    public void run(){
        //处理具体的逻辑
    }
}).start();
```



### 2、运行结果

![logcat](C:\Users\11937\Desktop\1.png)