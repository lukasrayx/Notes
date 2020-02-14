排序

- 初级排序
  - 选择排序
  - 插入排序
  - 希尔排序
- 快速排序
- 堆排序
- 归并排序
  - 原地归并
  - 自顶向下
  - 自底向上
- 优先队列

查找

+ 二叉树查找
  + 2-3查找树
  + 红黑二叉树
+ 散列表

图

+ 无向图
+ 有向图
+ 最小生成树
+ 最短路径

正则表达式



## Aufbau eines c-programms

```c
#include<stdio.h>

int n, s;

int main()
{
    int i;

    scanf("%i", &n);
    i = 1;
    s = 0;
    while (i <= n)
    {
        s = s+i*i;
        i++;
    }
    printf("%d",s );
    return 0; 
}

```

***Aktuelle Parameter:*** 			int x=10;

在主调函数中调用一个函数时，函数名后面括号中的参数称为“实际参数”（简称“实参”）。

实参可以是[常量](https://baike.baidu.com/item/常量)、[变量](https://baike.baidu.com/item/变量)或[表达式](https://baike.baidu.com/item/表达式)， 无论实参是何种类型的量，在进行[函数调用](https://baike.baidu.com/item/函数调用)时，它们都**必须具有确定的值**， 

***Formale Parameter:*** 在定义函数或过程的时候命名的参数。通俗讲就是一个记号。  int a ;



递归：

```c
#include<stdio.h>

int x,i;

void B();

void A(){
    x = 2 * x;
    printf("%d\n", x);
    if (i <4){
        i++;
        B();
    }
    printf("%d\n", x);
}

void B(){
    int x; 

    x = 1;
    printf("%d\n", x);
    A();
    printf("%d\n", x);
}


int main(){    
    i = 1;
    x = 2;
    A();      /*4,1,8,1,16,1,32,32,1,32,1,32,1,32*/
    return 0;
}
```

```c
#include<stdio.h>
void g(int x, int y, int *z);

void f(int x, int *y){
    int u;
    if (x>0){
        f(x-1, &u);
        g(x-1, u, y);
    }
    else *y =1;
}

void g(int x, int y, int *z){
    int u;
    if (x>0){
        f(x-1, &u);
        *z = u + y;
    }
    else *z =1;
}

int main(){
    int e, a;
    scanf("%i", &e);
    f(e, &a);
    printf("a = %d\n", a);
    return 0;
}
```

+ simpleType
  + char
  + int
    + Signed short int
    + Unsigned int
  + enum
  + Float, double, long double
  + 1 byte = 8 bits
+ Feld-Typen ( ArrayType )
+ Verbund-Typen ( RecordType )
+ Dynamische Datentypen ( PointerType )





















