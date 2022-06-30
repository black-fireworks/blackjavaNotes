# 泛型
概念
```
泛型也就是参数化类型.
将类型由具体类型进行参数话,类似于方法中的变量参数.
在使用时传入具体类型即可.
```

## 泛型类
泛型类示例
```java
/**
 * @author 黑色的小火苗
 * 该类为 泛型类演示类
 * 泛型标识可用使用其他字符,这里就用常用的 T 来代表泛型
 */
public class GenericsClassDemo<T> {
    private T data;

    public T getData() {
        return data;
    }

    public void setData(T data) {
        this.data = data;
    }


    /**
     * 泛型类的使用
     */
    public static void main(String[] args) {
        // 先实例化一个对象
        GenericsClassDemo<Integer> demo = new GenericsClassDemo<>();
        demo.setData(20);
        // 输出结果: 20
        System.out.println(demo.getData());
    }
}
```

## 泛型接口
概述
```
泛型接口在定义上与泛型类差不多.
```
泛型接口示例
```java
/**
 * @author 黑色的小火苗
 * 该接口为演示泛型接口
 */
public interface GenericsInterfaceDemo<T> {
    /**
     * 获取数据
     * @return 泛型类型
     */
    T getData();
}
```
实现上面泛型接口有两种方式
```java
/**
 * @author 黑色的小火苗
 * 第一种直接传入指定类型
 */
public class GenericsInterfaceDemoImpl implements GenericsInterfaceDemo<String> {
    private final String USER = "root";

    @Override
    public String getData() {
        return USER;
    }
}

/**
 * 在实现接口时不传入指定类型,而是在实例化对象时根据情况传入指定类型
 * @param <T>
 */
class GenericsInterfaceDemoImpl1<T> implements GenericsInterfaceDemo<T>{
    private T data;
    @Override
    public T getData() {
        return data;
    }
}
```

## 泛型方法
概念
```
当我们不确定之后传入的类型到底为什么类型时可用使用泛型来代替.
不适用 object 是因为传入后还需要进行判断,我们使用泛型则不需要.
```
泛型方法语法:
```
// 参数类型可以为泛型
权限修饰符 静态修饰符|不加静态修饰符 泛型 返回值类型 泛型方法名(参数类型 参数名){
} 
```

泛型方法示例
```
/**
 * @author 黑色的小火苗
 * 泛型方法演示类
 */
public class GenericsMethodDemo {
    public static <T> T sum(T a,T b){
        return a;
    }
    
    public <T> void print(T a){
        System.out.println(a);
    }
    
    private <T> T get(T a){
        return a;
    }
}
```

## 泛型限制类型
通配符
```
类型通配符是使用？代替方法具体的类型实参。
1 <? extends Parent> 指定了泛型类型的上届
2 <? super Child> 指定了泛型类型的下届
3 <?> 指定了没有限制的泛型类型
```

在使用泛型时限制它传入限制
```
例如:
    必须是某某类的子类或 某某接口的实现类，

格式:
    <T extends 类或接口1 & 接口2>
```