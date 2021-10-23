# 003

C-States werden mit DVFS umgesetzt.



# 004_Prozessoren_x86

1.What is Register-Memory Architektur and Load-Store Architektur

**Load-Store architecture** CPU只允许用load/store指令来与memory(Flash、RAM)交互，而CPU的运算全部都是在寄存器中完成。也就是说，CPU运算的操作数只能全部来自寄存器，而且结构也只能保存在寄存器中。所以，倘若要把RAM两个数据相加，结果还保存到内存中，就需要先将内存中的数据通过load指令将内存数据加载到寄存器中，计算结束后，再将保存结果寄存器的内容通过store指令存储在RAM中。举一个ARM指令的例子如下。ADD R0,R1,R2，单纯载入和加载，risc

**Register-Memory architecture** CPU的运算操作数可以全部都是寄存器，也允许其中的一个操作数在memory中。所以，CPU可以通过其他指令来与memeory交互，这种架构的指令集相对复杂。举一个X86指令的例子如下。add mem,reg

**Register-plus-Memory architecture** CPU的运算操作数可以全部都是寄存器，也可以全部都是memory，还可以两者都有。而且，寄存器、memory的size是可变的，可以是单字节、两个字节、四个字节。所以，CPU和memeory的交互比"Register-Memory architecture"更灵活。这种架构的指令集非常复杂，在译码过程中效率很低。举一个VAX指令的例子如下。XORL3 (R3)+,(R4)+,(R5)+

2.

3.

4.



