# Übung 4

## 1.a

## 1.b

```c
#include<stdio.h>

int main(){
  int n, i;
  int result = 1;
  pirntf("Enter your number:");
  scanf("%i", &n);
  
  for(i = 1; i <= n; i++){
    result = result * i;
  }
  printf("%i", result);
  
  return 0;
}
```



## 1.c

```c
#include<stdio.h>

int main(){
  int n, i, j;
  printf("Enter your number:");
  scanf("%i", &n);
  
  for(i = 1; i <=n; i++){
    for(int j = 1; i <= n; j++){
      printf("%i\t", i*j)
    }
    printf("\n");
  }
  
  return 0;
}
```



## 1.d

```c
#include<stdio.h>

int main(){
  for (int i = 2; i <= 1000; i++){
    int prime = 1;
    for(int j = 2; j < i; j++){
      if(i % j == 0){
        prime = 0;
      }
    }
    if(prime == 1){
      printf("%i is prime. \n", i);
    }
  }
}
```

## 2

```C
#include<stdio.h>

int main(){
  int matches, turn;
  scanf("%d", &matches);
  turn = 1;
  while (matches > 0){
    if(turn == 1){
      int z = (matches - 1) % 4;
      if (z ==0){
        z = 1;
      }
      matches = mathces - z;
      turn
    }
  }
}
```















