Many times we have used == and equals() without knowing in details what exactly these does and is it generating correct results as per our expectation or not.  In this blog, we will clear all your doubts related to equals() and == and next time you can use this confidently and be sure of your implementaion.

Let's start with the basics. 

> As JAVA is an Object Oriented Language and the Parent class of all classes is **Object** class which contains few predefined methods. Equals is one the **predefined method of Object class** whereas "==" is a **comparison operator** like we use other operators such as greater than(>),  less than (<), etc. 

Since equals is a method, it can be only called on objects and can't be used with the primitive data types (int, byte, short, long, float, double, boolean and char). Whereas "==" can be used on primitive data types as well as for objects.

> For **String and Wrapper classes** - Equals() method is already overwridden and does CONTENT COMPARISON (comapres value contained in class object). For all other classes, Equals() does REFERENCE COMPARIOSN (compares address). 

> For Primitive data types, "==" does CONTENT COMPARISON. If "==" is used with objects, it will do REFERENCE COMPARISON.


Got confused? Let's break it down in simpler terms. When we create a object using **new** keyword, it gets created in HEAP memory and and the object name is created in stack which contains the address of object in heap. Where as when a primitive variable is declared, its stored in STACK along with the value. 
