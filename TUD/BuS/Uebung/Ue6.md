# Vorbereitung



 











# 6.1

![](https://i.imgur.com/3Z64r6P.jpg)

a)

```c
Sem_t S(1); //Sem for Semaphore
Sdown();
fahren();
Sup();
//beide Richtung so
//xor: 相同为0.不同为1
```



b)

```c
Sem_t S1(1), S2(1)
 
R1
S1.down();
fahren();
S1.up();

R2:
S2.down();
fahren();
S2.up;
```



3）

```c
Sem_t S1(3), S2(3);
...wie b)
```



