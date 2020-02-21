# 数据库安全性

### 安全标准

+ TCSEC/TDI标准

+ CC标准
  + 安全功能要求
  + 安全保证要求



### 数据库安全性控制

+ 用户识别和鉴别
+ 存取控制： DAC， MAC
+ 自主存取控制：通过GRANT和REVOKE语句实现
+ 授权和回收
+ 数据库角色
+ 强制存取控制

### 审计Audit Log：

将用户对数据库的操作记录在上面

### 数据加密

+ 替换方法
+ 置换方法
+ 混合方法

规则：

+ 任何查询至少要涉及 N(N 足够大 ) 个以上的记录
+ 任意两个查询的相交数据项不能超过 M 个
+ 任一用户的查询次数不能超过 1+(N-2)/M



# 数据库的完整性

- 实体完整性： PRIMARY KEY
- 参照完整性： FOREIGN KEY
  - 违约处理：
    - 拒绝执行 ON DELETE NO ACTION
    - CASCADE操作 ： ON DELETE CASCADE
    - 设置空值 SET-NULL
- 用户定义完整性
  - NOT NULL
  - UNIQUE
  - CHECK： CHECK (Ssex IN (‘ 男’，‘女’ ) )   /*Ssex 只允许取 ' 男 ' 或 ' 女 ' */



建立学生登记表 Student ，要求学号在 90000~99999 之间 ，姓名不能取空值，年龄小于 30 ，性别只能是“男”或“女”。

```sql
CREATE TABLE Student
(Sno NUMERIC(6) 
 CONSTRAINT C1 CHECK (Sno BETWEEN 90000 AND 99999) ， 
 Sname CHAR(20) 
 CONSTRAINT C2 NOT NULL ， 
 Sage NUMERIC(3) 
 CONSTRAINT C3 CHECK (Sage < 30) ， 
 Ssex CHAR(2) CONSTRAINT C4 CHECK (Ssex IN ( ' 男 ' ， ' 女 ')) ，
 CONSTRAINT StudentKey PRIMARY KEY(Sno) )；

```

修改表 Student 中的约束条件，要求学号改为在 900000~999999 之间，年龄由小于 30 改为小于 40:

```sql
ALTER TABLE Student 
DROP CONSTRAINT C1; 
ALTER TABLE Student 
ADD CONSTRAINT C1 CHECK (Sno BETWEEN 900000 AND 999999) ， 
ALTER TABLE Student 
DROP CONSTRAINT C3; 
ALTER TABLE Student 
ADD CONSTRAINT C3 CHECK (Sage < 40) ；

```

### 域中的完整性约束： CREATE DOMAIN

```sql
建立一个性别域，并声明性别域的取值范围
CREATE DOMAIN GenderDomain CHAR(2) 
CHECK (VALUE IN (' 男 ' ， ' 女 ') );

删除域 GenderDomain 的限制条件 GD 。
ALTER DOMAIN GenderDomain 
DROP CONSTRAINT GD;

在域 GenderDomain 上增加限制条件 GDD 。 
ALTER DOMAIN GenderDomain 
ADD CONSTRAINT GDD CHECK (VALUE IN ( '1' ， '0') );

```

### 触发器：

- 触发器（ Trigger ）是用户定义在关系表上的一类 由事件驱动的特殊过程
- 触发事件： INSERT 、 DELETE 、 UPDATE
- 触发器类型
  - 行级触发器（ FOR EACH ROW ）
  - 语句级触发器（ FOR EACH STATEMENT ）

```sql
CREATE TRIGGER < 触发器名 >
{BEFORE | AFTER} < 触发事件 > ON < 表名 >
FOR EACH {ROW | STATEMENT} 
［ WHEN < 触发条件 > ］ < 触发动作体 >

定义一个 BEFORE 行级触发器，为教师表 Teacher 定义完 整性规则“教授的工资不得低于 4000 元，如果低于 4000 元，自动 改为 4000 元”。 
CREATE TRIGGER Insert_Or_Update_Sal 
BEFORE INSERT OR UPDATE ON Teacher  /* 触发事件是插入或更新操作 */
FOR EACH ROW /* 行级触发器 */ 
AS BEGIN /* 定义触发动作体，是 PL/SQL 过程块*/
IF (new.Job=' 教授 ') AND (new.Sal < 4000) THEN 
new.Sal :=4000; 
END IF; 
END;

```

同一个表上的多个触发器激活时遵循如下的执行顺序：

+ 首先执行BEFORE触发器
+ 激活触发器的SQL语句
+ 最后执行AFTER触发器

删除触发器：`DROP TRIGGER < 触发器名 > ON < 表名 >;`



# 规范化

**relational Model**: R(U, D, DOM, F)   简化：R( U, F )

*U*: 属性名集合  ==*DOM*==：属性向域的映像集合	*F*：属性间数据的依赖关系集合

### 数据依赖类型：

- 函数依赖Functional Dependency（FD）
- 多值依赖Multivalued Dependency（MVD）

### 关系模式中存在的问题：

- 冗余过大
- 更新异常Update Anomalies
- 插入异常Insertion Anomalies
- 删除异常Deletion Anomalies

**原因：** 某些数据依赖引起

**解决方法：**通过分解关系模式来消除不合适的数据依赖

ie： Student<U, F>

​		  U = ｛ Sno, Sdept, Mname, Cname, Grade ｝

​           F ＝｛ Sno → Sdept, Sdept → Mname, (Sno, Cname) → Grade ｝

  变成：

​			S （ Sno ， Sdept ， Sno → Sdept ） ;

​		    SC （ Sno ， Cno ， Grade ，（ Sno ， Cno ） → Grade ） ;

​			DEPT （ Sdept ， Mname ， Sdept→ Mname ）

### 规范化：

规范化理论正是用来改造关系模式，通过分解关系模式来 消除其中不合适的数据依赖，以解决插入异常、删除异常 、更新异常和数据冗余问题。

### 函数依赖：

设 R(U) 是一个属性集 U 上的关系模式， X 和 Y 是 U 的子集。 若对于 R(U) 的任意一个可能的关系 r ， r 中不可能存在两 个元组在 X 上的属性值相等， 而在 Y 上的属性值不等， 则 称 “ X 函数确定 Y” 或 “ Y 函数依赖于 X” ，记作 X→Y 。

#### 平凡函数依赖与非平凡函数依赖

在关系模式 R(U) 中，对于 U 的子集 X 和 Y ， 

如果 X→Y ，但 Y $\not\subseteq$ X ，则称 X→Y 是非平凡的函数依赖 

若 X→Y ，但 Y $\subset$ X, 则称 X→Y 是平凡的函数依赖



*bsp:* 在关系 SC(Sno, Cno, Grade) 中，

- 非平凡函数依赖： (Sno, Cno) → Grade 

- 平凡函数依赖： (Sno, Cno) → Sno (Sno, Cno) → Cno



- 若 X→Y ，则 X 称为这个函数依赖的决定属性组， 也称为决定因素（ Determinant ）。 
- 若 X→Y ， Y→X ，则记作 X←→Y 。 
- 若 Y 不函数依赖于 X ，则记作 X\→Y 。



### 完全函数依赖与部分函数依赖：

在 R(U) 中，如果 X→Y ，并且对于 X 的任何一 个真子集 X’ ，都有 X’ Y, 则称 Y 对 X ***完全函数依赖*** ，记作X^F^ Y。

 若 X→Y ，但 Y 不完全函数依赖于 X ，则称 Y 对 X ***部分函数依赖***，记作 X^P^ Y 

### 传递函数依赖：

在 R(U) 中，如果 X→Y ， (Y $\subset$ X) ,Y→X Y→Z ， 则称 Z 对 X 传递函数依赖。 记为： X传递 → Z

*注 : 如果 Y→X ， 即 X←→Y ，则 Z 直接依赖于 X 。*

**主属性**： 包含在任何一个候选码中的属性 ，称为***主属性***（ Prime attribute ）

**全码：** 整个属性组是码，称为***全码***（ All-key ）



## 范式：

范式是符合某一种级别的关系模式的集合

**分类：**

- 1NF：  atomic
- 2NF：  非主属性完全依赖于码
- 3NF ： 消除传递依赖。
- BCNF：决定子为主键
- 4NF:  消除非平凡非函数依赖的多值依赖MVD
- 5NF



**3NF的定义**

关系模式 R<U ， F> 中若**不存在**这样的码 X 、 属性组 Y 及非主属性 Z （ Z $\sub$	Y ） , 使得 X→Y ， Y→Z

成立， Y → X ，则称 R<U ， F> ∈ 3NF 。

若 R∈3NF ，则每一个非主属性既不部分依赖于码也不 传递依赖于码。



### ==多值依赖==：

设 R(U) 是一个属性集 U 上的一个关系模式， X 、 Y 和 Z 是 U 的子集，并且 Z ＝ U － X － Y 。关系模式 R(U) 中多值依赖 X→→Y 成立，当且仅当对 R(U) 的任一关系 r ，给定的一对 （ x ， z ）值，有一组 Y 的值，这组值仅仅决定于 x 值而与 z 值无关。

**判定方法：对于任意关系中，如果存在两个元组（就是行），记为A,B，如果他们的某一属性X的值相等，那么我们交换它们另外的属性Y的值后，得到的新的两个元组，在表中是可以在原来的表中找到与它们相匹配的元组的**

若 X→→Y ，而 Z ＝ φ ，则称 X→→Y 为***平凡的多值依赖***，否则称 X→→Y 为***非平凡的多值依赖***

 **例子：**关系模式 WSC （ W ， S ， C ）

W 表示仓库， S 表示保管员， C 表示商品

假设每个仓库有若干个保管员，有若干种商品，每个保管员保管所在的仓库的所有商品，每种商品被所有保管员保管

![](https://tva1.sinaimg.cn/large/0082zybpgy1gbwu9a2pybj31060megnm.jpg)



（ 1 ）多值依赖具有对称性

若 X→→Y ，则 X→→Z ，其中 Z ＝ U － X － Y 

（ 2 ）多值依赖具有传递性

若 X→→Y ， Y→→Z ， 则 X→→Z –Y

（ 3 ）函数依赖是多值依赖的特殊情况。

若 X→Y ，则 X→→Y 。 

（ 4 ）若 X→→Y ， X→→Z ，则 X→→Y $\bigcup$ Z 。 

（ 5 ）若 X→→Y ， X→→Z ，则 X→→Y $\bigcap$ Z 。 

（ 6 ）若 X→→Y ， X→→Z ，则 X→→Y-Z ， X→→Z -Y 。



## ==数据依赖的公理系统==

### 逻辑蕴含：

对于满足一组**函数依赖** F 的关系模式 R <U ， F> ，其任何一个关系 r ，若函数依赖 X→Y 都成立 , （即 r 中任意两元组 t ， s ，若 t [ X ] =s [ X ]，则        t [ Y ]  =s [ Y ]），则称 F **逻辑蕴含** X →Y。

换句话说：

**函数依赖**:  *属性集 **α** 决定属性集 **β** ,则称有函数依赖 α→β*

**逻辑蕴含:** *F能推出 原<u>不直观存在于</u> 函数依赖集F 中的函数依赖 α →→ β,则称α→→β被函数依赖集F逻辑蕴含*

**函数依赖的闭包 F+:** *由关系模式R<u>直观得到</u>的**函数依赖F**所推出的所有隐含的或未隐含的(直观的)函数依赖的集合* 

*举例：F中有α–>β,β–>ω， 则函数闭包F+中存在α–>ω*





### Armstrong 公理系统：

关系模式 R <U ， F > 来说有以下的推理规则：

- A1. 自反律（ Reflexivity ）：若 Y $\subseteq$  X $\subseteq$  U ，则 X →Y 为 F 所蕴含。(叫大推小更确切):    集合A能推出其集合子集b 
- A2. 增广律（ Augmentation ）：若 X→Y 为 F 所蕴含，且 Z  U ，则 XZ→YZ 为 F 所蕴含。(加了也不影响)
- A3. 传递律（ Transitivity ）：若 X→Y 及 Y→Z 为 F 所蕴含 ，则 X→Z 为 F 所蕴含。

根据 A1 ， A2 ， A3 这三条推理规则可以得到下 面三条推理规则：

- 合并规则：由 X→Y ， X→Z ，有 X→YZ 。（ A2 ， A3 ）(合并右边)
- 伪传递规则：由 X→Y ， WY→Z ，有 XW→Z 。（ A2 ， A3 ）(左边加一点)
- 分解规则：由 X→Y 及 Z$\subseteq $Y ，有 X→Z 。（ A1 ， A3 ）(分解右边)



### 函数依赖闭包：

在关系模式 R<U ， F> 中为 F 所逻辑 蕴含的函数依赖的全体叫作 ***F 的闭包***，记为 F^+^  

设 F 为属性集 U 上的一组函数依赖， X $\subseteq$ U ， X~F~ ^+^  ={ A|X→A 能由 F 根据 Armstrong 公理导出 } ， X ~F~^+^ 称为属性集 X 关于函数依赖集。

### 关于闭包的引理：

设 F 为属性集 U 上的一组函数依赖， X ， Y $\subseteq$  U ， X→Y 能 由 F 根据 Armstrong 公理导出的充分必要条件是 Y $\subseteq$  X~F~^+^

**用途**： *将判定 X→Y 是否能由 F 根据 Armstrong 公理导出的 问题，转化为求出 X F + 、判定 Y 是否为 X F + 的子集的 问题*



### 函数依赖集等价：

定义 6.14 如果 G + =F + ，就说函数依赖集 F 覆盖 G （ F 是 G 的覆盖，或 G 是 F 的覆盖），或 F 与 G 等价。

引理 6.3 F + = G + 的充分必要条件是 F $\subseteq$  G + ，和 G $\subseteq$  F +



### 最小依赖集：

如果函数依赖集 F 满足下列条件，则称 F 为一 个极小函数依赖集。亦称为最小依赖集或最小覆盖。

(1) F 中任一函数依赖的右部仅含有一个属性。

(2) F 中不存在这样的函数依赖 X→A ，使得 F 与 F{X→A} 等价。

(3) F 中不存在这样的函数依赖 X→A ， X 有真子集 Z 使得 F-{X→A}∪{Z→A} 与 F 等价。



**[ 例 ]** 关系模式 S<U ， F> ，其中： U={ Sno ， Sdept ， Mname ， Cno ， Grade } ， F={ Sno→Sdept ， Sdept→Mname ， (Sno ， Cno)→Grade }   设 F’={Sno→Sdept ， Sno→Mname ， Sdept→Mname ， (Sno ， Cno)→Grade ， (Sno ， Sdept)→Sdept} 

F 是最小覆盖，而 F’ 不是。 因为： F ’ - {Sno→Mname} 与 F ’ 等价 F ’ - {(Sno ， Sdept)→Sdept} 也与 F ’ 等价

### 极小化过程:

每一个函数依赖集 F 均等价于一个极小函数依赖集 F~m~ 。此 F~m~ 称为 F 的最小依赖集。

- (1) 逐一检查 F 中各函数依赖 FD i ： X→Y ，若 Y=A1 A 2 …A k ， k > 2， 则用 { X→A j |j=1 ， 2 ，…， k} 来取代 X→Y 。
- (2) 逐一检查 F 中各函数依赖 FD i ： X→A ，令 G=F-{X→A} ，若 AX G + ， 则从 F 中去掉此函数依赖。
- (3) 逐一取出 F 中各函数依赖 FD i ： X→A ，设 X=B1 B2 …B m ，逐一考查 B i （ i=l ， 2 ，…， m ），若 A  （ X-B i ） F ， 则以 X-B i取代 X 。

**[ 例 ]**  F = {A→B ， B→A ， B→C ， A→C ， C→A} F m1 、 F m2 都是 F 的最小依赖集： Fm1 = {A→B ， B→C ， C→A} Fm2 = {A→B ， B→A ， A→C ， C→A} 

- F 的最小依赖集 F m 不唯一 
- 极小化过程 ( 定理 6.3 的证明 ) 也是检验 F 是否为极小依 赖集的一个算法



## 模式的分解

- 把低一级的关系模式分解为若干个高一级的关系模式的方 法不是唯一的
- 只有能够保证分解后的关系模式与原关系模式等价，分解 方法才有意义

### 关系模式分解的标准

三种模式分解等价的定义：

- ⒈ 分解具有无损连接性 
- ⒉ 分解要保持函数依赖 
- ⒊ 分解既要保持函数依赖，又要具有无损连接性



**定义 6.16** 关系模式 R<U,F> 的一个分解： ρ={ R1 <U1 ,F1 > ， R2 <U2 ,F2 > ，…， Rn <Un ,Fn >}， 不存在U~i~ $\subseteq$  U~j~ , F~i~ 为F在U~i~ 上的投影。

**定义 6.17** 函数依赖集合 {X→Y | X→Y $\in$  F^+^ ∧ XY $\subseteq$ U~i~ } 的一个覆盖 F~i~ 叫作 F 在属性 U~i~ 上的投影



例： S-L （ Sno ， Sdept ， Sloc ）

F={ Sno → Sdept , Sdept → Sloc , Sno → Sloc}

 S-L∈2NF

==分解方法==可以有多种：

1. S-L 分解为三个关系模式： SN(Sno) SD(Sdept) SO(Sloc)
2. SL 分解为下面二个关系模式： NL(Sno, Sloc) DL(Sdept, Sloc)
3. 将 SL 分解为下面二个关系模式： ND(Sno, Sdept) NL(Sno, Sloc)
4. （<u>接下</u>）



### 具有无损连接性的模式分解:

关系模式 R < U , F > 的一个分解 ρ={ R1 <U1 ,F1 > ， R2 <U2 ,F2 > ，…， Rn <Un ,Fn >}若 R 与 R1 、 R2 、…、 Rn 自然连接的结果相等，则称关系 模式 R 的这个分解 ρ 具有***无损连接性（ Lossless join ）***

- 具有无损连接性的分解保证不丢失信息 
- 无损连接性不一定能解决插入异常、删除异常、修改复杂、数 据冗余等问题

### 保持函数依赖的模式分解:

设关系模式 R<U,F> 被分解为若干个关系模式 R1 <U1 ,F1 > ， R2 <U2 ,F2 > ，…， Rn <Un ,Fn >（其中 U=U1 ∪U2 ∪…∪U n ，且不存在 U i  U j ， F i 为 F 在 Ui 上的投影），若 F 所逻辑蕴含的函数依赖一定也由分解得 到的某个关系模式中的函数依赖 F i 所逻辑蕴含，则称关系 模式 R 的这个分解是**<u>保持函数依赖的</u>**（ Preserve dependency ）

- 4。(<u>接上</u>)  将 SL 分解为下面二个关系模式： ND(Sno, Sdept) DL(Sdept, Sloc) 这种分解方法就<u>保持了函数依赖</u>

  

- 如果一个分解具有无损连接性，则它能够保证不丢失信息 
- 如果一个分解保持了函数依赖，则它可以减轻或解决各种异 常情况 
- 分解具有无损连接性和分解保持函数依赖是两个互相独立的 标准。具有无损连接性的分解不一定能够保持函数依赖；同 样，保持函数依赖的分解也不一定具有无损连接性。



（接上“分解方法”）

- 第 1 种分解方法既不具有无损连接性，也未保持函数依赖，它不是原关系模式的一个等价分解 
- 第 2 种分解方法保持了函数依赖，但不具有无损连接性 
- 第 3 种分解方法具有无损连接性，但未持函数依赖 
- 第 4 种分解方法既具有无损连接性，又保持了函数依赖



### 分解算法：

- 算法 6.2 判别一个分解的无损连接性 算法 
- 6.3 （合成法）转换为 3NF 的保持函数依赖的分解。 算法
-  6.4 转换为 3NF 既有无损连接性又保持函数依赖 的分解 算法 
- 6.5 （分解法）转换为 BCNF 的无损连接分解 算法 
- 6.6 达到 4NF 的具有无损连接性的分解

### 小结：

- 若要求分解具有无损连接性，那么模式分解一定能够 达到 4NF 
- 若要求分解保持函数依赖，那么模式分解一定能够达 到 3NF ，但不一定能够达到 BCNF 
- 若要求分解既具有无损连接性，又保持函数依赖，则 模式分解一定能够达到 3NF ，但不一定能够达到 BCNF









