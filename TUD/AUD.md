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



- 当函数结束，函数体里的变量都会被销毁
- 命令行编译：gcc hello.c -o hello      ./hello



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



# 递归：

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
  + const: integer-konstanten
  + enum：`enum tagName{element1, element1, ...}`
  + Float, double, long double
  + 1 byte = 8 bits
+ Feld-Typen ( ArrayType )
+ Verbund-Typen ( RecordType )
+ Dynamische Datentypen ( PointerType )



# **Enum**: 

在C 语言中，枚举类型是被当做 int 或者 unsigned int 类型来处理的，所以按照 C 语言规范是没有办法遍历枚举类型的。不过在一些特殊的情况下，枚举类型必须连续是可以实现有条件的遍历。

```c
/*先定义枚举类型，再定义枚举变量*/
enum DAY
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
};
enum DAY day;


/*定义枚举类型的同时定义枚举变量*/
enum DAY
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
} day;


/*省略枚举名称，直接定义枚举变量*/
enum
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
} day;


#include <stdio.h>
#include <stdlib.h>
int main(){
    enum COLOR{
        red=1, yellow, green
    } color;

    printf("Please enter your fav. color:(1. red 2. yellow 3. green)");
    scanf("%d",&color);

    switch (color)
    {
    case red:printf("your fav. color is red!");  break;
    case yellow:printf("your fav. color is yellow!"); break;
    case green:printf("your fav. color is green!"); break;
    default:printf("you do not have fav. color!");break;
    }

    return 0;
}

```



**signed**意思为有符号的，也就是第一个位代表正负，剩余的代表大小，例如：signed int 大小区间为-128-127

**unsigned**意思为无符号的，所有的位都为大小，没有负数，例如：unsigned int 大小区间为：0-255

当然 **默认为signed**



- Float: 4 byte
- double : 8 byte
- long double : 10 byte

Feld ( Array ): eine Folge von Daten

- `int Feld[4] = { 1, 2, 7, 5}`
- `char Letter[6]`
- `Feld[2] = 7;`
- `Const int Feld[4] = { ... }   kann man int weglassen`
- `Typedef int array[4];  array Feld;`

# Verbund ( Structure, Union ) 

结构体struct，用户自定义的可用的数据类型

Oder:  结构体是用户根据实际需要自己定义的复合数类型；

- `Struct Beispiel { ... } a,b, c;`

- `Struct Beispiel x, y, z;`

- ```c
  struct tag { 
      member-list
      member-list 
      member-list  
      ...
  } variable-list ;
  ```

- ```c
  struct Books
  {
     char  title[50];
     char  author[50];
     char  subject[100];
     int   book_id;
  } book;
  ```

- UnionType: 允许您在相同的内存位置存储不同的数据类型

- ```c
  union [union tag]
  {
     member definition;
     member definition;
     ...
     member definition;
  } [one or more union variables];
  ```

- ```c
  typedef struct kfz_typ{
    char hersteller[20];
    enum {pkw, bus, lkw} art;
    float preis;
    union{
      short int vmax;
      short int sitzplaetze;
      float zuladung;
    } eigenschaft;
  } kfz;
  
  kfz auto1, auto2, auto3;
  
  auto1.art =pkw;
  auto1.eigenschaft.vmax = 180;
  
  auto2.art = lkw;
  auto2.eigenschaft.sitzplaetze = 45;
  
  auto3.art = lkw;
  auto3.eigenschaft.zuladung = 25.5f
  ```

**通常使用指针的方式赋值**

```c
struct Student *pst；  //pst所指向的结构体变量中的sid这个成员
pst->sid=1001；
strcpy(pst->name,"lisi")；
pst->age=19；
```







# Dynamische Datentypen:指针

- **指针**Pointer是一个变量，其值为<u>另一个变量的地址</u>，就像其他变量或常量一样，您必须在使用指针存储其他变量地址之前，对其进行声明。
- &（变量名）：取地址                 *（变量名）：取值
- Int *p = &x;     ==>      int *p ;      p = &x ; 

![](https://tva1.sinaimg.cn/large/0082zybpgy1gc6mr2ebynj31d00u0gqt.jpg)

![](https://tva1.sinaimg.cn/large/0082zybpgy1gc6mreyv08j317g0pqdih.jpg)

![](https://tva1.sinaimg.cn/large/0082zybpgy1gc6mrsfmi0j31p80tqgsa.jpg)

![](https://tva1.sinaimg.cn/large/0082zybpgy1gc6mryiqrfj31c60j60vm.jpg)

```c
#include<stdio.h>

void increment(int a){
  a++;
}

int main(){
  int a = 10;
  increment(a);

  printf("%d\n", a);
} //输出为10，a 并未 +1

void increment1(int *p){
  (*p)++;
}

int main(){
  int a = 10;
  increment1(&a); // a= 10 +1 = 11
}

void swap (int *a, int *b) { ... }
```

```c
#include<stdio.h>

int arr[] = {5, 6, 7, 8, 9};
int *p = &arr[0];

void move_p(int *p, int arr[]){
  p = &arr[1]; //*p = arr[1]; 才输出 p = 6 
}

int main(){
  move_p(p, arr);

  printf("%d\n", *p);  // p = 5
}

//ODER:
int* move_p(int *p, int arr[]){
  p = &arr[1];
  return p;
}

int main(){
  p = move_p(p, arr);

  printf("%d\n", *p);  // p = 6
}

//ODER
void move_p(int **pointer, int arr[]){
  *pointer = &arr[1];
}

int main(){
  int *p = &arr[0];
  move_p(&p, arr);  // p = 6
}
```

```c
#include <stdio.h>
 
int main ()
{
   int  var = 20;   /* 实际变量的声明 */
   int  *ip;        /* 指针变量的声明 */
 
   ip = &var;  /* 在指针变量中存储 var 的地址 */
 
   printf("Address of var variable: %p\n", &var  );
 
   /* 在指针变量中存储的地址 */
   printf("Address stored in ip variable: %p\n", ip );
 
   /* 使用指针访问值 */
   printf("Value of *ip variable: %d\n", *ip );
 
   return 0;
}

//Address of var variable: bffd8b3c
//Address stored in ip variable: bffd8b3c
//Value of *ip variable: 20
```

 ```c
  typedef int feld[100];
  tyedef feld *P_feld;
  P_feld a;
  
  int main(){
    a = (P_feld) malloc(sizeof(feld));
    (*a)[2] = 7;
    
    free(a); /* Speicherfreigabe, 释放之前调用 calloc、malloc 或 realloc 所分配的内存空间。 */
  }
  
  /*  P_feld : Zeigertyp, a ist vom Typ P_feld und sie bezeichnet einen Speichenrplatz, der als Wert die Anfangsadresse eines Speicherbereichs aufnehmen kann  */
  /* sizeof(feld)=100 */
  
 ```

  ```c
  #include <stdio.h>
  #include <stdlib.h>
  
  typedef struct ele *zeiger;
  typedef struct ele{
    int zahl;
    zeiger next;
  } element;
  
  int a, b; zeiger r;
  
  void A(int x, int y, int *z){
    int hilf; zeiger p;
    
    hilf = (x + y) * *z;
    p = (zeiger) malloc(sizeof(element));
    p ->zahl = hilf; // indirekter Zugriff, Dereferenzierung
    p ->next = r;  // gleichbedeutend mit: (*p).zahl=hilf;
    r = p;
    
    if (hilf < 100){
      *z = *z + 5; // z ist Referenzparameter, deshalb hier
                   // Zugriff auf den Wert mit*
      A(x + y, 10, z); /* aber hier rekursiver Aufruf von A mit drittem Parameter als Referenzparameter, also Uebergabe einer Adresse, die in z gespeichert ist! */
      *z = 2 * *z;
    }
  }
  
  int main(){
    a = 5;
    b = 6;
    r = (zeiger) malloc(sizeof(element));
    r ->zahl = 7; // gleichbedeutend mit (*r).zahl=7;
    r ->next = NULL;
    A(a, b, &b);
    return 0;
  }
  
  //malloc函数其实就是在内存中找一片指定大小的空间，然后将这个空间的首地址给一个指针变量，这里的指针变量可以是一个单独的指针，也可以是一个数组的首地址，这要看malloc函数中参数size的具体内容。
  ```

- malloc函数：

  -  **void \*malloc(size_t size)** 分配所需的内存空间，并返回一个指向它的指针。

  - **size** -- 内存块的大小，以字节byte为单位。

  - ```c
    #include <stdio.h>
    #include <string.h>
    #include <stdlib.h>
     
    int main()
    {
       char *str;
     
       /* 最初的内存分配 */
       str = (char *) malloc(15);
       strcpy(str, "runoob");
       printf("String = %s,  Address = %u\n", str, str);
     
       /* 重新分配内存 */
       str = (char *) realloc(str, 25);
       strcat(str, ".com");
       printf("String = %s,  Address = %u\n", str, str);
     
       free(str);
     
       return(0);
    }
    ```

    

- free()函数：

  - ```c
    void free(void *ptr)
    ```

  - 函数 **void free(void \*ptr)** 释放之前调用 calloc、malloc 或 realloc 所分配的内存空间。

  - **ptr** -- 指针指向一个要释放内存的内存块，该内存块之前是通过调用 malloc、calloc 或 realloc 进行分配内存的。如果传递的参数是一个空指针，则不会执行任何动作。

- ->  :  “->”是一个整体，它是用于指向结构体子数据的指针，用来取子数据。

  换种说法，如果我们在C语言中定义了一个结构体，然后申明一个指针指向这个结构体，那么我们要用指针取出结构体中的数据，就要用到“->”。

  问题中的p=p->next ，意思是将p指向的一个结构体实例中的自数据next赋值给p。（是复制一个相同的数据区域，而不是指向同一个数据区域）

  - ![](https://tva1.sinaimg.cn/large/0082zybpgy1gc6pxzld17j30go05at9p.jpg)



# Einfach-verkettete Listen:

- Jedes Element der Liste neben dem Schluesselwert(Key) und evtl. zugehoerigen Daten(data) einen Zeiger auf das nachfolgende Listenelement(next)

- ```c
  typedef struct nodeelem *Ptr;
  typedef struct nodeelem {
    int kdy;
    Ptr next;
    int data;
  }node;
  ```

- ```c
  Ptr h,p,q;
  int n,i;
  
  p -> data = 6;
  q = p -> next;
  ```

- ```c
  scanf("%i", &n);
  q = (Ptr) malloc(sizeof(node));
  h = q;
  q -> key = n;
  q -> next = NULL;
  for (i = 1; i <= 3; i++)
  {
    scanf("%i", &n);
    p = (Ptr) malloc(sizeof(node));
    p -> key = n;
    p -> next = NULL;
    q -> next = p;
    q = p;
  }
  ```



# Doppelt-verkettete Listen:

wenn die Daten nicht nur in einer Richtung durchlaufen werden können, sondern in beiden Richtungen. 

```c
typedef struct nodeelem *LPtr;
typedef struct nodeelem{
  int key;
  LPtr next;
  LPtr prev;
  ... data;
}node;

LPtr h, p, q;

//aufbau einer doppelt-verketteten Liste

scanf("%i", &n);
q = (LPtr) malloc(sizeof(node));
q -> key = n;
q -> prev = NULL;
h = q;
for (i=1; i <= 10; i++)
{
  scanf("%i", &n);
  p = (LPtr) malloc(sizeof(node));
  p -> key = n;
  q -> next = p; 
  p -> prev = q;
  q =p;
  q -> next = NULL;
}
```



# Tree:

Mit Hilfe des Strukturtyps **Baum** laesst sich eine große Klasse von verzweigten Strukturen erfassen.

**先序遍历preorder： 根->左->右**    

**中序：左 -> 根 -> 右**  <u>从小到大排列</u>

**后序 :左 -> 右 -> 根**

```c
#include<stdio.h>
#include<stdlib.h>

typedef struct node
{
  int data;
  struct node* left;
  struct node* right;
} Node ;

/*tree的结构通过遍历（先后中序）来查看*/
void preorder(Node* node){
  if (node != NULL) {
    printf("%d\n", node -> data);
    preorder(node -> left);
    preorder(node -> right);
  }
}

void inorder(Node* node){
  if (node != NULL){
    inorder(node -> left);
    printf("%d\n", node -> data);
    inorder(node -> right);
   }
}
 
void postorder(Node* node){
  if (node != NULL){
    postorder(node -> left);
    postorder(node -> right);
    printf("%d\n", node -> data);
  }

}

int main() {
  Node n1;  //ie. struct node n1;
  Node n2;
  Node n3;
  Node n4;

  n1.data = 5;
  n2.data = 6;
  n3.data = 7;
  n4.data = 8;

n1.left = &n2;
n1.right = &n3;
n2.left = &n4;
n2.right = NULL;
n3.left = NULL;
n3.right = NULL;
n4.left = NULL;
n4.right = NULL;

preorder(&n1);
inorder(&n1);
postorder(&n1);
}
```



#### 二叉搜索树🌲 binary search tree（BST)

> 根 > 左
>
> 根 < 右

  ```c
#include<stdio.h>
#include<stdlib.h>

typedef struct node{
  int data;
  struct node* left;
  struct node* right;
} Node;

typedef struct{
  Node* root;
} Tree;

void insert(Tree* tree, int value){
  Node* node = malloc(sizeof(Node)); /*malloc：当函数结束时，Node不会被销毁*/
  node -> data  = value;
  node -> left  = NULL;
  node -> right = NULL;

  if (tree -> root == NULL){
    tree -> root = node;
  }
  else {
    Node* temp = tree -> root;
    while (temp != NULL)
    {
      if (value < temp -> data){
        if (temp -> left == NULL){
            temp -> left = node;
            return;
        }
        else {
          temp = temp -> left;
        }
      }
      else {
        if (temp -> right == NULL){
          temp -> right = node;
          return;
        }
        else {
          temp = temp -> right;
        }       
      }
    }   
  }
}

int main(){
  int arr[7] = {6, 3, 8, 2, 5, 1, 7};
  Tree tree;
  tree.root = NULL;

  int i;
  for ( i = 0; i < 7; i++)
  {
    insert(&tree, arr[i]);
  }
}
  ```

```c
int get_height(Node* node){
  if(node == NULL){  //递归出口
    return 0; 
  }
  else{
    int left_h  = get_height(node -> left);
    int right_h = get_height(node -> right);
    int max = left_h;
    if(right_h > max){
      max = right_h;
    }
    return max + 1;
  }
}
```

```c
int get_maximum(Node* node){
  if(node ~= NULL){ //假设都是正数
    return -1;
  }
  else{
    int m1 = get_maximum(node -> left);
    int m2 = get_maximum(node -> right);
    int m3 = node -> data;
    if(m2 > max) { max = m2; }
    if(m3 > max) { max = m3; }
    return max;
  }  
}
```















```c
typedef struct nodeelem *Bptr;
typedef struct nodeelem {
  int key;
  BPtr left, right;
  ... data;
} node;
```

```c
/*Wir wollen eine Funktion hoehe speifizieren, welche die Berechnung der Hoehe( Anzahl der Knoten auf dem laengsten Pfad von der Wurzel zu einem Blatt) eines Baumes des Typs node berechnen soll.*/

int hoehe(BPtr wz)
{
  int h1, h2;
  if ( wz == NULL ) return 0;
  h1 = hoehe(wz -> right);
  h2 = hoehe(wz -> right);
  return max(h1, h2) + 1;
}



typedef struct nodeelem *BPtr;
typedef struct nodeelem {
  int key;
  BPtr left, right;
  ... data;
} node;

int hoehe( ... ) { ... }
void eingabe( BPtr *wz) { ... }

int main(){
  int h; BPtr w;
  eingabe(&w);
  h = hoehe(w);
  ...
}
```

```c
typedef enum { S, A, C, a, b, c} set_of_symbols;
typedef enum {r1, r2, r3, r4, r5, r6, no} set_of_rules;

typedef struct nodeelem *pointer_to_node;
typedef struct trailelem *pointer_to_trail;

typedef struct nodeelem{
  set_of_symbols label;
  set_of_rules rule;
  pointer_to_trail next;
} node;

typedef struct trailelem{
  pointer_to_node item;
  pointer_to_trail next;
} trail;
```













## Modularisierungskonzept

### Definitionsmodul

Im Definitionsmodul ( oder : Header-File ) filename.h wird die Schnittstelle des Moduls festgelegt. Das geschicht durch die Angabe der Objekte, die von außen sichtbar und nutzbar sein sollen.

```c
typedef struct ele *pushdown;

void CreatePushdown(pushdown *s);
void Push(pushdown *s, int x);
void Pop(pushdown *s, int *x);

int Empty(pushdown s);
```

```c
/*Das Modul pushdown koennte dann von einem anderen Modul beispielsweise folgendermaßen importiert und benutzt werden*/

#include "pushdown.h"

pushdown t, u;
int x;
...
{...
  CreatePushdown(&u);
  CreatePushdown(&t);
  Push(&u, 25);
  Push(&t, 7);
  ...
  if (!Empty(u)){
    Pop(&u, &x);
    Push(&t, x);
  }
  ...
}
```



### Implementierungsmodul

Diese Programmierung bleibt fuer andere Module unsichtbar und ist nicht zugreifbar oder veränderbar 

- Das Implementierngsmodul ( filename.c ) muss das Definitionsmodul ( filename.h ) ebenfalls mit ***#include*** "filename.h" importieren.
- Im Implementierungsmodul müssen alle Beschreibungen opaker Datentypen und alle Funktionsdeklarationen zu dem im Definitionsmodul enthaltenen Funktionskoepfen enthalten sein.
- Alle anderen im Definitionsmodul enthaltenen Namen dürfen *nicht* mehr erscheinen.

```c
#include <stdlib.h>
#include "pushdown.h"

typedef struct ele{
  int key;
  pushdown next;
} element;

void CreatePushdown(pushdown *s){
  *s = NULL;
}

void Push(pushdown *s, int x){
  pushdown top;
  
  top = (pushdown) malloc(sizeof(element))
  top -> key = x;
  top -> next = *s;
  *s = top;
}

void Pop(pushdown *s, int *x)
{
  pushdown top;
  
  top = *s;
  *x = (*s) -> key;
  *s = (*s) -> next;
  free(top);
}

int Empty(pushdown s)
{
  return s == NULL;
}

```















































