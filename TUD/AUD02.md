# Sortieren

- Externem Sortieren
- Internem Sortieren : Quicksort, Heapsort

## Quicksort

> 是对冒泡排序的改进，通过一趟排序将数据分割成两部分，其中一部分的所有数据比另一部分小，然后再对这两部分进行quicksort，整个排序递归进行
>
> 左标记的作用是找到一个比basic大的数字，右标记则相反

```c
void quicksort(int a[], int L, int R)
{
  int i, j, temp, x, k;
  
  i = L; j = R;
  k = (L + R) / 2; x = a[k];
  
  do {
    while (a[i] < x) i++;
    while (a[j] > x) j--;
    if (i <= j){
      temp = a[i];
      a[i] = a[j];
      a[j] = temp;
      i++, j--;
    }
  }
  while (i <= j);
  
  if (L <j ) quicksort(a, L, j);
  if (R >j ) quicksort(a, i, R);
}

//do{...} while(condition);  if condition=false, break.

```

## Heapsort

> Heap:     1. complete binary tree.     2. Parent > children
>
> Heapify : 左孩子右孩子选一个最大值和父节点交换
>
> Parent = (i - 1) / 2,  child1 = 2i + 1,  child2 = 2i + 2

```c
#include<stdio.h>

void swap(int arr[], int i, int j){
  int temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}

void heapify(int tree[], int n, int i){
  if (i >= n)
  {
    return;
  }
  
  int c1 = 2 * i + 1;
  int c2 = 2 * i + 2;
  int max = i;
  if (c1 < n && tree[c1] > tree[max])
  {
    max = c1;
  }
  if (c2 < n && tree[c2] > tree[max])
  {
    max = c2;
  }
  if (max != i)
  {
    swap(tree, max, i);
    heapify(tree, n, max);
  }
}

void build_heap( int tree[], int n){
  int last_node = n - 1;
  int parent = (last_node - 1) / 2;
  int i;
  for (i = parent ; i >= 0 ; i--) {
    heapify(tree, n, i);
  }
}

void heap_sort(int tree[], int n){
  build_heap(tree, n);
  int i;
  for (i = n - 1; i >= 0; i--)
  {
    swap(tree, i, 0);
    heapify(tree, i, 0);
  }
  
  /*int arr[n];
  for (int i = 0; i < n; i++)
  {
    arr[i] = tree[0];
    swap(tree, 0, n-i-1);
    ...
  }*/  
  //我打算把最后一个数drop掉，单独弄一个array
}

int main()
{
  int tree[] = {4, 10, 3, 5, 1, 2};
  int n = 6;
  heap_sort(tree, n);

  int i;
  for (i = 0; i < n; i++)
  {
     printf("%d\n", tree[i]);
  }

  return 0;
}
```



```c
#define K 100;

void sinkenlassen(int a[], int l, int r)
{
  int i, j, j, loop;
  
  i = l;
  h = a[i];
  loop = 1;
  while(loop)
  {
    j = 2*i+1;
    if(j>r) break;
    
    if(j<r) 
      if(a[j] < a[j+1]) j++;
  
  	if (h > a[j]) break;
    else {
      a[i] = a[j];
      i = j;
    }
  }
  
  a[i] = h;
}

void Heapsort(int a[], int n)
{
  int li, re, x;
  
  li = n/2;
  re = n-1;
  while(li>0){
    li--;
    sinkenlassen(a, li, re);
  }
  while (re >0){
    x = a[0];
    a[0] = a[re];
    a[re] = x;
    re = re-1;
    sinkenlassen(a, 0, re);
  }
}

int main()
{
  int a[k];
 Heapsort(a, k);
}
```

# Suchen

- der Datenbestand eine feste Größe hat und 有序查找
- der Datnbestand eine veränderbare Größe hat 无序查找

Naive algorithms: 不考虑复杂度 - 但是能把问题解决的算法，比如穷举之类的。



### KMP algorithm

pattern: ababc

Prefix:

- a ： 最长公共前后缀 0 
- ab ： 最长公共前后缀0
- aba ： 最长公共前后缀1
- abab :  最长前缀aba  最长后缀bab  二位前缀ab 后缀ab，最长公共前后缀2
- ababc ： 最长公共前后缀 0 

最长公共前后缀列表Prefix table： 0 0 1 2 0   -->   -1 0 0 1 2

T:   a  b   a    a   c   a   b   a   b    c    a    c

P:   a   b   a   b   c

​       -1 0   0    <u>1</u>   2

​                  a   <u>b</u>    a  b   c

​                        a   <u>b</u>    a  b   c

​                              <u>a</u>   b    a  b   c 

​                                    <u>a   b   a  b   c</u>

​                                               a   b    a  b   c



Pattern: ababcabaa 

Prefix table: 001201231

代码实现：

```c

```



















































