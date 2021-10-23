# GENERAL

### V7

Operatorpräzedenz : ¬ > ∧ > ∨

与或非的运算

Neutrale Elemente 𝒆 = 𝟏 und 𝒏 = 𝟎

布尔函数 Schaltfunktion

Schaltalgebra

Schaltnetz

MUX

Addierer，Paralleladdierer

Speicherglieder

### 

### V9-Architekturkonzepte

Verbindungsstruktur: Stern, Bus, Ring, Baum, Mesh/Array (Feld), Crossbar

Kontrollflußarchitektur - Datenflußarchitektur

Parallelität: 

- BLP Die Bitstellen eines Datums oder mehrere Daten werden parallel verarbeitet.

  ILP Mehrere Befehle eines Kontrollflusses werden parallel ausgefu¨hrt.

  MT Parallele Ausfu¨hrung mehrerer Teile (Threads) eines Kontrollflusses (Multithreaded).

  MP Parallele Ausfu¨hrung mehrere Programme, Prozesse (Multiprocessing).

  DFP Die Datenflußverarbeitung ist vom Konzept her hochparallel.

Parallelarchitekturen nach Flynn

- SISD: Single Instruction – Single Data (von-Neumann Rechnerkonzept).
- MISD Multiple Instruction – Single Data (SystolicArrays, KI-Beschleuniger).
- SIMD Single Instruction – Multiple Data
- MIMD Multiple Instruction – Multiple Data, Multiprocessor und Multicomputer.

Klassifikation nach Verbindungsnetzwerken

Klassifikation nach W. Giloi

Operationsprinzipien nach W. Giloi

PMS Klassifikation (Processor, Memory, Switch)

Von Neumann Rechnerkonzept

- 哈弗架构和冯·诺依曼架构最大的不同就是内存分为独立的指令内存和数据内存。
- 和冯·诺依曼架构相比，哈佛架构因为指令内存的读取和数据内存的读写分开，一定程度上可以保证指令的连续性，不会因为需要访问内存上的数据造成指令堵塞。

Kriterien des von Neumann Rechners  1-5

Struktur des von Neumann Rechners

- CPU
  - Befehlsprozessor (Steuerwerk)
  - Datenprozessor (Rechenwerk)
- Speicher (Daten + Befehle)
- Systembus
  - Datenbus
  - Addessbus
  - Steuerbus

Struktur mit I/O-Prozessor und Busaufteilung







### V10 Befehlsatz

操作数有三种方式提供：立即数、寄存器存放的数据、内存中的数据

Register Operand，Memory Operand

MOV AX,0FFFFH AX 即为寄存器操作数，操作数本身存放于寄存器中，在指令中只是给出了几个位的代码来表示它具体存放在哪个寄存器中。

Main memory used for composite data ¤ Arrays, structures, dynamic data

Endian 	字节序

- Big-Endian :  将高序字节存储在起始地址（高位编址）
- Little-Endian : 将低序字节存储在起始地址（低位编址）

Registers vs. Memory

Immediate Operands

- 立刻数是一个常量，可以写成十进制（D），十六进制（H），八进制（O），二进制（B）。例如：ADD AX，0FFH；其中的0FFH就是立刻数。

  通俗一点的理解：一个你可以凭空捏出来给CPU，不需要CPU去各种寄存器取的常量数据。

  注意一点：立即数只能作为源操作数，不能放在目的操作数位置。也就是指令中结果所存放的数据位。

Instruction Format: Register (R-type)

- ¤ opcode: operation code 
- ¤ rd: destination register number 
- ¤ funct3: 3-bit function code (additional opcode) 
- ¤ rs1: the first source register number 
- ¤ rs2: the second source register number 
- ¤ funct7: 7-bit function code (additional opcode)

Instruction Format: Immediate (I-type)

- immediate: constant operand, or offset added to base address

Shift Operations : slli, srli, srai

AND Operations, OR Operations, XOR Operations 异或, Conditional Operations

Compiling If Statements

Compiling Loop Statements

Basic Blocks: a sequence of instructions with 1. 2.

More Conditional Operations

- blt rs1, rs2, L1
- bge rs1, rs2, L1

Signed vs. Unsigned





### V11

Procedure Calling： steps required 1-6

? Procedure Call Instructions

Calling Convention调用约定： Register Usage/ Stack/ Stack Frame/ 

Aligned Access 对齐访问

Data Alignment: Structs 		数据对齐

RISC-V Addressing

RISC vs. CISC







# FRAGEN

Buffe 和 Cache的区别

**Buffer**

- Buffer是特指内存中临时存放的IO设备数据——包括读取和写入

- （缓冲区）是系统两端处理**速度平衡**（从长时间尺度上看）时使用的。它的引入是为了减小短期内突发I/O的影响，起到**流量整形**的作用。比如生产者——消费者问题，他们产生和消耗资源的速度大体接近，加一个buffer可以抵消掉资源刚产生/消耗时的突然变化。
- buffer还有一个作用是等到生产者生产了足够多的东西之后批量送给消费者，以减小多次少量输送引起的overhead。
- Buffer的核心作用是用来缓冲，缓和冲击。比如你每秒要写100次硬盘，对系统冲击很大，浪费了大量时间在忙着处理开始写和结束写这两件事嘛。用个buffer暂存起来，变成每10秒写一次硬盘，对系统的冲击就很小，写入效率高了，日子过得爽了。极大缓和了冲击。

**Cache**

- （缓存）则是系统两端处理**速度不匹配**时的一种**折衷策略**。因为CPU和memory之间的速度差异越来越大，所以人们充分利用数据的局部性（locality）特征，通过使用存储系统分级（memory hierarchy）的策略来减小这种差异带来的影响。
- buffer还有一个作用是等到生产者生产了足够多的东西之后批量送给消费者，以减小多次少量输送引起的overhead。
- 把当前最常用的东西，放在最容易拿的地方，这就是cache。（正如台湾的翻译，快取）
- Cache的核心作用是加快取用的速度。比如你一个很复杂的计算做完了，下次还要用结果，就把结果放手边一个好拿的地方存着，下次不用再算了。加快了数据取用的速度。









# VOCAL

ISA : instruction Set Architecture

Firmware 固件

DCB: 二进码十进数（英语：Binary-Coded Decimal

HEX: 十六进制码

Octal Code: 八进制码

Umschaltzeichen （escape symbols）: 转义符号

Stellenwert : 对数

Redix： 根，解

Vorzeichenbehaftet： 带有符号的

Multiplexer：MUX，数据选择器，多路选择器，逻辑功能是在地址选择信号的控制下，从多路数据中选择一路数据作为输出信号

Festwertspeicher：ROM 只读存贮器

Speicherglieder：存储元件

Belegungen：占用，分配

Schaltnetz：组合逻辑电路

LMB: local memory bus 本地内存总线

TLB: Translation Lookaside Buffer 转译后备缓冲器,CPU的一种缓存

- ITLB : Instruction TLB
- UTLB : Unified TLB
- DTLB : Data TLB

FPU： Float Point Unit，浮点运算单元

BIOS(Basic Input Output System)

bne, bdq cmp 相当于流程图的菱形

BEQ指令是“相等或为0则跳转指令”

```c++
cmp r1,r2  
bne copy_loop
//这个cmp搭配下边的bne指令构成了如果r1≠r2则执行bne指令，跳转到copy_loop函数处执行。否则，就跳过下边的bne指令向下执行。
  
cmp r0,r1
beq clean_bss
//如果r0=r1，就执行beq，跳转到clean_bss函数处执行，否则跳过beq向下执行。
```

















