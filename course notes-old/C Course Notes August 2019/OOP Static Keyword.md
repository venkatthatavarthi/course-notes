# OOP - Static Keyword

class MyClass{
private int _hiddenField; INSTANCE
public string Property01{get;set} INSTANCE
public void Method01(){} INSTANCE

    public MyClass(){}    // constructor

}

var m = new MyClass(){} // constructor
m = instance
m.Property01;
m.Method01();

Math.PI;
Math.Random()
Math.Round()
STATIC MEMBERS ATTACHED DIRECTLY TO MATH CLASS

class MyClass{
static public int Property01{get;set;} CLASS / STATIC
static public void DoThis(){} CLASS / STATIC
}

    MyClass.Property01;
    MyClass.DoThis();  
    					don't change with relation to instances

Mind Picture
user (instance) with PERSONAL SHOPPING BASKET
static count of TOTAL ITEMS IN STOCK

    user1 with instance1
    user2              2
    ...
    user100            100
    
    static MEMORYAVAILBLE