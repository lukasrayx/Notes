**相比面向过程POP（如C语言），面向对象OOP能够更好的在抽象的层面来分析问题，在程序实现中可以复用之前的代码**

Java舍弃了C语言中的指针，用引用来替代，还舍弃了运算符重载，多重继承（以接口取代）等，并增加了垃圾回收器功能，用于回收不再被引用的对象所占据的内存空间（自动）。

Java SE: Java Standard Edition

Java EE: Java Enterprise Edition

两种核心机制：

- JVM：Java Virtal Machine
- GC：Garbage Collection 垃圾收集机制

JDK :  Java Development kit （Java开发工具包）

JRE :  Java Runtime Environment (Java 运行环境)

JDK $\subset$ JRE $\sub$ JVM

注释： // ,  /* */

编译： javac xx.java 		运行 java xx

注释： ctr + /

强制转换：int i = 7;  byte b = (byte) i;

a=2;  b=++a;   --> a=3, b=3  先运算，再取值

a=2;  b=a++;   --> a=3, b=2  先取值，再运算

5 % -2  = 5 % 2 = 1

-5 % 2 = -1

'a' : char类型

"a" : 字符串

a^b : 异或  ab相同false ， ab不同true

![](https://i.imgur.com/5HCwdlA.jpg)

![](https://i.imgur.com/uIlepgA.jpg)

![](https://i.imgur.com/g7Y8evs.jpg)



## Day3，4

三元运算符： (条件)？表达式1: 表达式2

为true：表达式1， 为false：表达式2

```java
//求100以下所有质数
for(int i = 1; i < 100; i++) {	
	
	int count = 0;
	
	for(int j = 1; j <= i; j++) {
		if(i%j == 0) {
			count++;
		}
	}
	
	if(count == 2) {
		System.out.println(i);
	}
	
}
```

break; 跳出循环

continue;  跳出当前循环进入下一个

数组：

- 动态 ` int[] array = new int[5]`
- 静态 `int[] array = {1,2,3,4,5} ` 
- 长度：array.length



## Day5, 6, 7

**面向对象的三大特征：**

- 封装 Encapsulation
- 继承 Inheritance
- 多态 Polymorphism

现实生活中万物由原子构成，而java中由**类Class**构成

- 属性：对应**类**中的成员**变量**
- 行为：对应**类**中的成员**方法**   show**N**ame 驼峰命名
- **Field = 属性 = 成员变量**
- **Method = 成员方法 = 函数**



**对象的创建和使用**

使用 **new** + 构造器 创建一个新的对象（实例化），使用  **对象名.对象成员**  的方式访问对象成员（对象成员incl.  属性和方法）



`Person person = new Person()  `

声明一个Person类型的变量，变量名为person，实例化Person类，并给person赋值，赋值的值就是当前的实例,	 new Person()就是实例化Person类 (Person类之前已定义)



**属性：** 

- private： 该属性只能由该类的方法访问，**无法在其他类中调用**
- public：  该属性可以被该类以外的方法访问
- 变量
  - 成员变量
    - 实例变量（不以static修饰）：在类**实例化的对象中**才能使用
    - 类变量（以static修饰）：不需要类实例化成对象就可以使用，直接通过 `类名.属性` 使用（static方法只能访问static对象）
  - 局部变量：**只能在所属方法内使用**
    - 形参（方法签名中定义的变量）
    - 方法局部变量（在方法内定义）：必须手动初始化，无默认值
    - 代码块局部变量（在代码块内定义，类中直接用 { ... } 定义） 

**方法的重载 Overload：**

- Def：在一个类中，允许存在一个以上的同名方法，只要他们的**参数个数**或者**参数类型**不同即可
- 特点：与**返回值类型无关**，只看**参数列表**

**可变个数的参数**

- `public void printInfo(String[] args)`  用数组传递传递个边个数参数
- `public void printInfo1(String... args)`  用...方式传递可变个数参数，与数组使用方式相同
- `public void printInfo2(int d, String... args)` ...要放在最后

**包和引用import：**

- 类似文件夹，将语意相近的类class组织到包中，包可以包含类和子包，解决同名文件问题
- 通常小写，用.来分隔层次
- 引用：使用同一个包中的类，import可省略
- 引用： **import  package1.package2.className**
- 引用：**package.package1.className**
- 引用： **import package.***
- jdk中主要的包： java.lang(包含String, Math Integer等) / .net/ .io/ .util(包含实用工具类)/ .sql/ .applet/ .awt/ .text

**封装和隐藏**

- 使用声明private隐藏
- 再使用public类型的getXXX(){ return XXX }或setXXX() 实现对该属性的操作，加入逻辑控制
- 或者直接右键，Source，generate Getters and Setters

**访问权限修饰符：**

![](https://i.imgur.com/gys8fBg.jpg)



**关键字：this:**

- this表示当前对象，可以调用类属性，方法和构造器
- 在方法内部使用，表示对方法所属对象的引用
- 在构造器内部使用，表示构造器正在初始化的对象
- 1.在形参和成员变量重名是，必须用this
- 2.增强程序阅读性
- 3.在构造器中调用其他构造器

**继承：**

- public class 子类 extends 父类
- 父类方法重写 override
- 子类不能访问父类私有的

**关键字：super：**

- super可以访问调用父类的属性，方法和构造器
- 当父类子类出现同名成员时，可以用super加以区分
- super代表父类内存空间的标识
- super可以向上追溯父类的父类的父类...
- 在父类只有有参数构造可以使用的时候，子类必须显示的构造一个有参构造来调用父类的有参构造，且调用父类的构造要卸载第一行super().

![](https://i.imgur.com/cxI1Uoq.jpg)



![](https://i.imgur.com/k3VYP07.jpg)

![](https://i.imgur.com/mdn2Mgz.jpg)



**多态 Polymorphism**

![](https://i.imgur.com/2DiWC1s.jpg)

![](https://i.imgur.com/P0p6834.jpg)



**Object 类**

- Object是所有类的父类
- ![](https://i.imgur.com/kMwk6zb.jpg)



toString会重写父类的toString方法，返回一个你想要的String

toString的好处是在碰到“println”之类的输出方法时会自动调用，不用显式打出来，而getString()必须打出来xx.getString()



