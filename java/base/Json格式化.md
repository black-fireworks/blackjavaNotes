# JSON

    Json: JavaScript Object Notation JS对象简谱 是一种轻量级的数据交换格式

    JSON语法格式:
        JSON中一对大括号就是一个对象 括号中描述对象的属性,以键值对形式存在 
    
    格式:
        键与值之间用冒号链接,多个键值对之间使用逗号分割 
        键值对的键 应该使用引号引住 [ 可以不引住,但是在java解析中,不引住会报错,但是js可以正常解析 ] 
        键值对的值,可以是JS中的任意类型的数据

    示例:
        {
            "name": "名",
            "age": "14"
        }

当前演示中使用的实体类
```java
/**
 * @author blackFire
 * 这里是使用了 lombok jar 和 idea 的 lombok插件
 */
@Data
public class Person {
    private String name;
    private int age;

    /**
     * 为了方便示例,当创建这个对象实例时, name为张三 age 为17
     */
    public Person() {
        this.name = "张三";
        this.age = 17;
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

## Gson

```xml
<!-- 
    下载好jar导入或者使用 maven 从 pom 进行导入
 -->
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.8.9<</version>
</dependency>
```

使用示例:
```java
import com.google.gson.Gson;

import java.util.ArrayList;
import java.util.List;

/**
 * @author blackFire
 */
public class GsonFormatJsonTest {


    /**
     * object and json mutual conversion
     * java对象 和 json 字符串相互转换示例
     */
    public static void objectAndJsonMutualConversion(){
        // 将对象格式化为 Json 字符串
        String personJson = new Gson().toJson(new Person());
        System.out.println(personJson);

        // 将 json 字符转化为 java对象
        Person person = new Gson().fromJson(personJson, Person.class);
        System.out.println(person);
    }


    /**
     * object Array List and json mutual conversion
     * java对象数组列表 和 json 字符串相互转换示例
     */
    public static  void objectArrayAndJsonMutualConversion(){
        List<Person> persons = new ArrayList<>();
        int length = 5;
        // 向 列表添加 5 个实体对象
        for(int item =0; item < length; item++){
            persons.add(new Person("张三"+item, 17+item));
        }

        // 将 列表转换为 Json字符串
        String personJson = new Gson().toJson(persons);
        System.out.println(personJson);

        Person[] people = new Gson().fromJson(personJson, Person[].class);
        for (Person person : people) {
            System.out.println(person);
        }
    }




    public static void main(String[] args) {
        // 这里仅用来调用方法
        GsonFormatJsonTest.objectAndJsonMutualConversion();
        GsonFormatJsonTest.objectArrayAndJsonMutualConversion();
    }
}
```


## FastJson
```xml
<!-- 
    下载好jar导入或者使用 maven 从 pom 进行导入
-->
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.8.9<</version>
</dependency>
```

使用示例:
```java
import com.alibaba.fastjson.JSON;

import java.util.ArrayList;
import java.util.List;

/**
 * @author blackFire
 */
public class FastJsonFormatJsonTest {


    /**
     * object and json mutual conversion
     * java对象 和 json 字符串相互转换示例
     */

    public static void objectAndJsonMutualConversion(){
        // 将对象格式化为 Json 字符串
        String personJson = JSON.toJSONString(new Person());
        System.out.println(personJson);

        // 将 json 字符转化为 java对象
        Person person = JSON.parseObject(personJson, Person.class);
        System.out.println(person);
    }

    /**
     * object Array List and json mutual conversion
     * java对象数组列表 和 json 字符串相互转换示例
     */
    public static  void objectArrayAndJsonMutualConversion() {
        List<Person> persons = new ArrayList<>();
        int length = 5;
        // 向 列表添加 5 个实体对象
        for(int item =0; item < length; item++){
            persons.add(new Person("张三"+item, 17+item));
        }
        // 将列表转换为 json 字符串
        String personJson = JSON.toJSONString(persons);
        System.out.println(personJson);
        
        // 将json字符串转化为定长数组
        Person[] people = JSON.parseObject(personJson, Person[].class);
        for (Person person : people) {
            System.out.println(person);
        }
    }


    public static void main(String[] args) {
        // 这里仅调用方法
        FastJsonFormatJsonTest.objectAndJsonMutualConversion();
        FastJsonFormatJsonTest.objectArrayAndJsonMutualConversion();

    }
}
```