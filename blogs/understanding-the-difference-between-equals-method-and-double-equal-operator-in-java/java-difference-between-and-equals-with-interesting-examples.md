Many times we have used == and equals() without knowing in details what exactly these does and is it generating correct results as per our expectation or not.  In this blog, we will clear all your doubts related to equals() and == and next time you can use this confidently and be sure of your implementaion.

Let's start with the basics. 

> As JAVA is an Object Oriented Language and the Parent class of all classes is **Object** class which contains few predefined methods. Equals is one the **predefined method of Object class** whereas "==" is a **comparison operator** like we use other operators such as greater than(>),  less than (<), etc. 

Since equals is a method, it can be only called on objects and can not be used with the primitive data types (int, byte, short, long, float, double, boolean and char). Whereas "==" can be used on primitive data types as well as for objects.

Some oif the key points related to `Equals()` and `==` are below:

>> `Equals()`: Equals() method is already overridden for ***String and Wrapper classes(Byte, Short, Integer,Long, Float, Double, Boolean, Character)*** -  and does `CONTENT COMPARISON` (compares value contained in class object). For all other classes, Equals() does only `REFERENCE COMPARISION` ( if objects are pointing to same object).

>> `==`: It compares the value stored in Primitive data types variables. If "==" is used with objects, it matches the address of objects and see if both are pointing to a same object.


To completely understand the above point, you must know in brief, about memory allocation in JAVA. When we create a `object` using **`new`** keyword, it gets created in `HEAP memory` and  its `address` gets stored in `STACK` along with the `object name`. Whereas when a `primitive variable` is created, it gets stored in `STACK` along with the `actual variable value.` 


![Tech UnBlog - JAVA memory allocation for object and primitive types](https://raw.githubusercontent.com/TechUnBlog/articles/main/blogs/difference%20between%20equals%20and%20%3D%3D.png "Tech UnBlog - JAVA memory allocation for object and primitive types")


As you see in above image, a=10 is stored in stack whereas car object got created in HEAP and only its address is stored in stack.

So now we are clear on how the Object is stored and how its different from primitive type. Now let's start with examples.

Example : Comparing String value and integer value
   
```java
public class Example {
    public static void main(String[] args) {

        // primitive variable
        int num1 = 10;
        int num2 = 10;


        // String Object
        String str1 = new String("tech unblog");
        String str2 = new String("tech unblog");
        String str3 = str1;


        System.out.println(num1==num2);         // true
        System.out.println(str1==str2);         // false
        System.out.println(str1==str3);         // true
        System.out.println(str1.equals(str2));  // true

    }
}
```

![TechUnBlog - example1 memory allocation ](https://raw.githubusercontent.com/TechUnBlog/articles/main/blogs/example1.png "TechUnBlog - example1 memory allocation")

## Explanation of output

1. `num1==num2` : When == is used with integer variable; it matched the value and returned `true` as both `num1` and `num2` contains same value `10`.
2. `str1==str2` : In case of string objects, the values are same; but == matches the address when used with objects, and since the address of `str1` and `str2` is different, so it returned `false`
3. `str1==str3` : As `str1` and `str3` is pointing to same object and hence the address is same for both objects and so it returned `true`.
4. `str1.equals(str2)` : Since `str1` and `str2` contains same value and equals() is already overridden for String class  to matches content stored in object, so it returned `true`.

Pay attention to point `2` & `4`. See how == and Equals() gave different result when applied for same objects (str1 and str2).

Lets take another Example: StringBuffer and String comparison.

```java
public class Example {
    public static void main(String[] args) {

        // String Object
        String str1 = new String("tech unblog");
        String str2 = new String("tech unblog");
        String str3 = str1;


        //StringBuffer
        StringBuffer sb1= new StringBuffer("tech unblog");
        StringBuffer sb2= new StringBuffer("tech unblog");
        StringBuffer sb3= sb1;
        
        
        System.out.println(str1==str2);         // false
        System.out.println(sb1==sb2);           // false
        System.out.println(str1==str3);         // true
        System.out.println(sb1==sb3);           // true
        System.out.println(str1.equals(str2));  // true
        System.out.println(sb1.equals(sb2));    // false

    }
}
```

## Explanation of output

1. `str1== str2` and `sb1==sb2` both returned **`false`**. Its obvious as we discussed, that `==` compares address of the objects, and since both the objects are different (even though the value in them is same), == retuns false as they are represnting two different address.

2. `str1==str3` and `sb1==sb3` returned **`true`** as both the objects pointing to same address. 

3. `str1.equals(str2)` retuns **`true`**, as we discussed, that Equals() is already overridden for value comparison for `String and Wrapper Classes`.

4. `sb1.equals(sb2)` returns **`false`**, because in all other classes except String and wrapper, Equals() matches the reference if both the objects are pointing to same address or not. Since `sb1` and `sb2` are pointing to 2 differnet address, it reurned `false`.


## Conclusion:

### When to use `==` operator:

Use == only for comparing `primitive data types` or `checking reference equality`. By understanding the distinction between these two approaches, you can write more robust and reliable Java code. Happy coding!

### When to use `equals()` method:

Remember it's a mentod so can't be used on primitive types. Use equals() for String and Wrapper classes for mathing the values. For other classes, it will match the address of objects and not values. It's always recommended to Override the equals() menthod in customer classes 

