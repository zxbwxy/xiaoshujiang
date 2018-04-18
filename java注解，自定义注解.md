---
title: java注解，自定义注解
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---

## 引言
Annotation(注解)是JDK1.5及以后版本引入的。它可以用于创建文档，跟踪代码中的依赖性，甚至执行基本编译时检查。注解是以‘@注解名’在代码中存在的，根据注解参数的个数，我们可以将注解分为：标记注解、单值注解、完整注解三类。它们都不会直接影响到程序的语义，只是作为注解（标识）存在，我们可以通过反射机制编程实现对这些元数据（用来描述数据的数据）的访问。另外，你可以在编译时选择代码里的注解是否只存在于源代码级，或者它也能在class文件、或者运行时中出现（SOURCE/CLASS/RUNTIME）。
## Java内建注解

Java提供了三种内建注解。
1. @Override
当我们想要复写父类中的方法时，我们需要使用该注解去告知编译器我们想要复写这个方法。这样一来当父类中的方法移除或者发生更改时编译器将提示错误信息。

2. @Deprecated
当我们希望编译器知道某一方法不建议使用时，我们应该使用这个注解。Java在javadoc 中推荐使用该注解，我们应该提供为什么该方法不推荐使用以及替代的方法。

3. @SuppressWarnings
这个仅仅是告诉编译器忽略特定的警告信息，例如在泛型中使用原生数据类型。它的保留策略是SOURCE（译者注：在源文件中有效）并且被编译器丢弃。

## 自定义注解
要自定义一个注解，需要使用java提供的四个元注解，元注解的作用就是负责注解其他注解。Java5.0定义的四个元注解为：@Target、@Retention、@Documented、@Inherited这些类型和它们所支持的类在java.lang.annotation 包中可以找到。
1. @Documented 
指明拥有这个注解的元素可以被javadoc此类的工具文档化。这种类型应该用于注解那些影响客户使用带注释的元素声明的类型。如果一种声明使用Documented进行注解，这种类型的注解被作为被标注的程序成员的公共API。

2. @Target
指明该类型的注解可以注解的程序元素的范围。该元注解的取值可以为TYPE,METHOD,CONSTRUCTOR,FIELD等。如果Target元注解没有出现，那么定义的注解可以应用于程序的任何元素。
	
	> @Target(ElementType.TYPE)   //接口、类、枚举、注解
	> @Target(ElementType.FIELD) //字段、枚举的常量
	> @Target(ElementType.METHOD) //方法
	> @Target(ElementType.PARAMETER) //方法参数
	> @Target(ElementType.CONSTRUCTOR)  //构造函数
	> @Target(ElementType.LOCAL_VARIABLE)//局部变量
	> @Target(ElementType.ANNOTATION_TYPE)//定义元注解，只能用于注解类型元素上
	> @Target(ElementType.PACKAGE) ///包

3. @Inherited
指明该注解类型被自动继承。如果用户在当前类中查询这个元注解类型并且当前类的声明中不包含这个元注解类型，那么也将自动查询当前类的父类是否存在Inherited元注解，这个动作将被重复执行知道这个标注类型被找到，或者是查询到顶层的父类。

4. @Retention
指明了该Annotation被保留的时间长短。RetentionPolicy取值为SOURCE,CLASS,RUNTIME。

	> @Retention(RetentionPolicy.SOURCE)   //注解仅存在于源码中，在class字节码文件中不包含。
	> @Retention(RetentionPolicy.CLASS)     //默认的保留策略，注解会在class字节码文件中存在，但运行时无法获得，不能通过反射获取注解信息。
	> @Retention(RetentionPolicy.RUNTIME)  //注解会在class字节码文件中存在，在运行时可以通过反射获取到注解信息。

## 示例
创建自定义注解和创建一个接口相似，但是注解的interface关键字需要以@符号开头。我们可以为注解声明方法。下面是一个自定义注解的例子。
### 定义注解类
``` java
package com.annotation;

import java.lang.annotation.*;

@Documented
@Inherited
//JVM会读取注解,所以利用反射可以获得注解
@Retention(RetentionPolicy.RUNTIME)
//该注解可以作用于方法,类与接口
@Target({ElementType.METHOD, ElementType.TYPE})
public @interface MyAnnotation {
    //定义成员变量
    //成员变量可以通过default指定默认值
    //如果成员变量不指定默认值的情况下
    //我们在引用接口时则必须给没有默认值的成员变量赋值
    String strVal() default "a";

    String[] arrayVal() default "arr";

    MyAnnoEnum enumVal() default MyAnnoEnum.RED;

}

enum MyAnnoEnum {
    RED, GREEN
}
```
 - 注解方法不能带有参数；
 -  注解方法返回值类型限定为：基本类型、String、Enums、Annotation或者是这些类型的数组； 
 - 注解方法可以有默认值；  
 - 注解本身能够包含元注解，元注解被用来注解其它注解。

### 实体类

``` java
public class UseAnnotation {

    @MyAnnotation(strVal = "b", arrayVal = {"arr2", "arr3"}, enumVal = MyAnnoEnum.GREEN)
    public void method() {
        //do something
    }

}
```

### 解析注解


``` java
package com.annotation;

import java.lang.annotation.Annotation;
import java.lang.reflect.Method;

public class ParseAnnotation {

    public static void main(String[] args) {
        //解析注解
        //获得我们需要解析注解的类
        Class<UseAnnotation> clz = UseAnnotation.class;

        //解析Class
        //由于我们的注解是可以给类使用的,所以首先判断类上面有没有我们的注解
        //判断类上面是否有注解
        boolean clzHasAnnotation = clz.isAnnotationPresent(MyAnnotation.class);
        if(clzHasAnnotation){
            //类存在我们定义的注解
            //获得注解
            MyAnnotation clzAnnotation = clz.getAnnotation(MyAnnotation.class);
            //输出注解在类上的属性
            System.out.println("stringVal="+clzAnnotation.strVal()+"\tArrayVal="+clzAnnotation.arrayVal());
        }

        //解析Method
        //两种解析方法上的注解方式
        //获得类中所有方法
        Method[] methods = clz.getMethods();
        //第一种解析方法
        for(Method m : methods){
            //获得方法中是否含有我们的注解
            boolean methodHasAnnotation = m.isAnnotationPresent(MyAnnotation.class);
            if(methodHasAnnotation){
                //注解存在
                //获得注解
                MyAnnotation methodAnnotation = m.getAnnotation(MyAnnotation.class);
                System.out.println("stringVal="+methodAnnotation.strVal()+"\tArrayVal="+methodAnnotation.arrayVal());
            }
        }
        //第二种解析方式
        for(Method m : methods){
            //获得方法上所有注解
            Annotation[] annotations = m.getAnnotations();
            //循环注解
            for(Annotation a : annotations){
                //如果是我们自定义的注解
                if(a instanceof MyAnnotation){
                    //输出属性,需要强制装换类型
                    System.out.println("name="+((MyAnnotation)a).strVal()+"\tage="+((MyAnnotation)a).arrayVal());
                }
            }
        }
    }

}

```
