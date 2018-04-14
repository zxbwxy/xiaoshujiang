---
title: java开发总结
tags: java
grammar_cjkRuby: true
---

#### poi
POI读取Excel的实际行
try {  
    Workbook hwb = new HSSFWorkbook(  
            new FileInputStream("C:\\1.xls"));  
    Sheet sheet = hwb.getSheetAt(0);  
    //int rowCount = sheet.getPhysicalNumberOfRows();  
  
    int begin = sheet.getFirstRowNum();  
  
    int end = sheet.getLastRowNum();  
  
    for (int i = begin; i <= end; i++) {  
        if (null == sheet.getRow(i)) {  
            continue;  
        }  
        // do something  
    }  
} catch (FileNotFoundException e) {  
    e.printStackTrace();  
} catch (IOException e) {  
    e.printStackTrace();  
}  


#### java 判断对象是否是某个类的类型两种方法
一、

instanceof 运算符是用来在运行时指出对象是否是特定类的一个实例。instanceof通过返回一个布尔值来指出，这个对象是否是这个特定类或者是它的子类的一个实例。 

用法：
result = object instanceof class
参数：
result
必选项。任意变量。
object
必选项。任意对象表达式。
class
必选项。任意已定义的对象类。
说明：
如果 object 是 class 的一个实例，则 instanceof 运算符返回 true。如果 object 不是指定类的一个实例，或者 object 是 null，则返回 false。

 例如：
 Boolean b;  
String str = "foo";  
b = ( str instanceof String );   // true
b = ( str instanceof Object );   // also true
b = ( str instanceof Date );     // false, not a Date or subclass

注意：
1）null值不是任何对象的实例，所以下面这个例子返回了false，无论这个变量声明的是什么类型。
String s = null; 
if ( s instanceof String ) 
    // false, won't happen
2）instanceof也可以正确的报告一个对象是否是数组和特定的接口类型。
if ( foo instanceof byte[] )

二、

一般可能我们在使用java的RTTI技术时，都使用instanceof来判断一个对象是不是属于某个类，但是有时候这个类是继承于一个父类的，所以，不能严格判断出是不是自己的类，而不是自己的父类。这个时候就使用另一种思路也是不错的——getClass判断；当然肯定还有其他的方法来判断的，只是自己的总结。如果有好的其他方法请赐教。。
``` java
public class test {
    public static void main(String arg[]) {
        ClassA a = new ClassA();
        ClassB b = new ClassB();
        ClassC c = new ClassC();
        sayClass(a);
        sayClass(b);
        sayClass(c);
        System.out.println("---------------------------------");
        equalClass(a);
        equalClass(b);
        equalClass(c);
    }
    public static void sayClass(Object o){
        if(o instanceof ClassA){
            System.out.println("ClassA");
        }else if(o instanceof ClassB){
            System.out.println("ClassB");
        }
    }
    
    public static void equalClass(Object o){
        if(o.getClass().equals(ClassA.class)){
            System.out.println(o.getClass().getName());
        }else if(o.getClass().equals(ClassB.class)){
            System.out.println(o.getClass().getName());
        }else if(o.getClass().equals(ClassC.class)){
            System.out.println(o.getClass().getName());
        }
    }
}
class ClassA{
    ClassA(){};
}
class ClassB{
    ClassB(){};
}

class ClassC extends ClassA{
    ClassC(){};
}

ClassA
ClassB
ClassA
---------------------------------
Test.ClassA
Test.ClassB
Test.ClassC
```