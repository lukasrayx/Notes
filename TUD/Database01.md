# Introduction

**Disadvantages of keeping organizational information**

+ **Data redundancy and inconsistency**
+ **Difficulty in a accessing data**
+ **Data isolation**
+ **Integrity problems**
+ **Atomicity problems**

**Data Abstraction**

+ **Physical level** : how to save in disk
+ ***Logical level** : logical schema 
+ **View level** : views of user

**Instances and Schemas**

- **instance** : collection of information

- **schema** : description of data, using a fiven data model
    + physical schema
    + logical schema
+ **View schema**, aka subschema

**Data models**

+ **relational Model** 
+ **Object Relational Model**
+ **Object-Based Data Model**
+ **XML Model**
+ **Semistructured Data Model**



**SOME JARGONS**

**Entity, Attribute, Key, Domain, Entity Type, Entity Set, Relationship**

**Relationship between two Entity** : 1:1, 1:n , m:n



**DML** : Data manipulation language 

```sql
select instructor.ID, department.dept name 
from instructor, department 
where instructor.dept name= department.dept name and department.budget > 95000;
```



**DDL**  : to deﬁne tables, integrity constraints, assertions, etc.

```sql
create table department
     (dept name char (20), 
      building char (15), 
      budget numeric (12,2));
```



完整性约束

+ **实体完整性** ： 若属性 A 是基本关系 R 的主属性，则属性 A 不能取空值

+ **参照完整性**： 

  ​		若属性（或属性组） F 是关系 R 的外码，和关系 S 的主码（R 和 S 不一定是不同的关 系），则对于 R 中每个元组在 F 上的值必须为： 

  + 或者取空值（ F 的每个属性值<u>***均为***</u>空值） 

  + 或者等于 S 中某个元组的主码值

+ **用户定义完整性**

  + NOT NULL约束
  + UNIQUE约束
  + 值域约束

数据库系统的组成

+ DB
+ DBMS
+ APP
+ DMA
+ User



**DBMS** : 1) Storage manager component	2)Query processor component

**DBA** : Database Administrator, A ***person*** who has such central control over the system



# Relational Databases

## Relational Model

In the relational model the term <u>***relation***</u> is used to refer to a <u>table</u>, while the term ***<u>tuple</u>*** is used to refer to <u>a row</u>. Similarly, the term *<u>**attribute**</u>* refers to a <u>column</u> of a table.

**Component** : 笛卡尔元素中的值



D1 ×D2 ×…×D n 的子集叫作在域 D 1 ， D 2 ，…， D n 上的 关系，表示为 R （ D 1 ， D 2 ，…， D n ）

R ：关系名 

n ：关系的目或度（ **Degree** ）



**Domain**  : For each attribute of a relation, there is a set of permitted values, called the domain of that attribute.

**Atomic**  : elements of the domain are considered to be indivisible units.

**Superkey**  : a set of one or more attributes that, taken collectively, allow us to <u>identify uniquely a tuple</u> in the relation.

**Candidate keys**  : We are often interested in superkeys for which <u>no proper subset is a superkey</u>. Such minimal superkeys are called candidate keys.

**primary key**  : denote a candidate key that is chosen by the database designer as the principal means of identifying tuples within a relation.

**Foreign key** : 

+ Referencing relation
+ Referenced relation



| S^#^ | Name | Age  |
| :--- | ---- | ---- |
| 001  | Ryan | 17   |

**Primary key**: S^#^       **Super key** : (S^#^  , Age )

**All key**



关系模式可以形式化地表示为： R （ U ， D ， DOM ， F ）

**R** 关系名 **U** 组成该关系的属性名集合 **D** 属性组 **U** 中属性所来自的域 **DOM** 属性向域的映象集合 **F** 属性间的数据依赖关系集合



关系模式通常可以简记为 R (U) 或 R (A 1 ， A 2 ， …， An )

**R**: 关系名 A 1 ，         **A 2 ，…， A n** : 属性名



**常用的关系操作**

**查询**：选择、投影、连接、除、并、交、差 

**数据更新**：*插入、删除、修改 查*询的表达能力是其中最主要的部分 

***选择、投影、并、差、笛卡尔基***是 5 种基本操作



**Rferential integrity constraint**

**Foreign key constraint** : 

**Domain integrity constraint**  : An attr.'s value must be a value in the domain

**Entity integrity constraint** :  Every should have a primary key, and PK cannot be NULL

 

**Relational Algebra**  :

![](https://tva1.sinaimg.cn/large/006tNbRwgy1gbmto3jdtsj30z20q8wl3.jpg)



**差set-difference** : R -S = { t | t in R  ∧  t not in  S }

**Selection** : Or Restriction，选择满足条件的行, σ<sub>F</sub> (R) = { t | t in R  ∧  F(t) = ' 真 '} F : Condition

**Projection** : 选择若干属性（列）组成新的关系 ,    π<sub>A</sub> (R) = { t[A] | t in R }    A : Attr. Col. in R

​                          *( has to eleminate duplicates!!)*



**Join** : 

+ natural join: 自然连接是一种特殊的等值连接

  + 两个关系中进行比较的分量必须是相同的属性组
  + 在结果中把重复的属性列去掉

+ equijoin : 从关系 R 与 S 的广义笛卡尔积中选取 A 、 B 属性值相等***(AθB)***的元组

+ θ join : 从两个关系的笛卡尔积中选取属性间满足一定条件***(AθB)***的元组 

+ outer join : 如果把natural join中舍弃的元组也保存在结果关系中，而在其他属 性上填空值 (Null) ，这种连接就叫做外连接（ OUTER JOIN ）。

+ Left outer join : 如果只把<u>左边关系 R 中要舍弃的元组保留</u>就叫做左外连接

+ right outer join   : 如果只把<u>右边关系 S 中要舍弃的元组保留</u>就叫做右外连接



**除division** : 给定关系 R (X ， Y) 和 S (Y ， Z) ，R 与 S 的除运算得到 P(X) ，元组在 X 上分量值 x 的象集 Y x 包含 S 在 Y 上投影的集合，记作：R÷S = { t<sub>r</sub> [X] | t<sub>r</sub> in R  ∧  π<sub>Y</sub> (S) in Y<sub>x</sub> }。eg. 在关系 R 中， A 可以取四个值 {a1 ， a2 ， a3 ， a4}

+ a 1 的象集为 {(b 1 ， c2 ) ， (b 2 ， c3 ) ， (b 2 ， c1 )} 
+ a 2 的象集为 {(b 3 ， c7 ) ， (b 2 ， c3 )} 
+ a 3 的象集为 {(b 4 ， c6 )} 
+ a 4 的象集为 {(b 6 ， c6 )}

S 在 (B ， C) 上的投影为 :    { (b1 ， c2) ， (b2 ， c1) ， (b2 ， c3) }

只有 a 1 的象集包含了 S 在 (B ， C) 属性组上的投影，所以R÷S ={a1 }                                  <!--通常处理all问题-->




























