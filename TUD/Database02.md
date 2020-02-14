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



