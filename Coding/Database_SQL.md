### DDL, Basic Schema Definition 

```sql
mysql -uroot -p  -- 密码yutianlei

create schema, table, view, index
drop schema, table, view, index
alter table

一些条件： primary key(attr.1, attr.2), unique取值唯一，foreign key(Cid) references Course(Cno)

数据类型：char, varchar, int, smallint, numeric, real, float,      date, time, double precision

numeric (12,2) 总位数为12，小数点后为2位的数，也就是说整数位最大是10位。

显示当前搜索路径： show serch_path
这是搜索路径：set sertch_path to "S-T", public;


create table department
		(dept name varchar (20), 
     building varchar (15), 
     budget numeric (12,2), 
     primary key (dept name));
     

     
     
insert into instructor values (10211, ’Smith’, ’Biology’, 66000);
			
delete from student;
show databases;
show tables;
drop databese;
drop table table_name;
delete from table_name where conditions;
use database_name;
insert into table_name(xxx) values (xxx);
select xxx from table_name;
id int primary key auto_increment; #自增
alter table r add A D; #A is the name of attr. D is type
alter table r drop A;
select distinct dept_name from instructor; 
#elimination of duplicates.
select all dept_name from instructor; 
#dupl. not remove, the same as select dept_name


create table instructor
     (ID varchar (5), 
      name varchar (20) not null, 
      dept name varchar (20), 
      salary numeric (8,2), 
      primary key (ID), 
      foreign key (dept name) references department);
      
create table teaches
		(ID varchar (5), 
     course id varchar (8), 
     sec_id varchar (8), 
     semester varchar (6), 
     year numeric (4,0), 
     primary key (ID, course id, sec id, semester, year), 	
     foreign key (course id, sec id, semester, year) references section, 
     foreign key (ID) references instructor);
     
#create index
CREATE [UNIQUE] [CLUSTER] INDEX < 索引名 > ON < 表名 >(< 列名 >[< 次序 >][,< 列名 >[< 次序 >] ] …) ；
drop index studentname;
					
```



### Queries： 单表查询

```sql
select name 
from instructor 
where dept name = ’Comp. Sci.’ and salary > 70000;

select name, instructor.dept name, building 
from instructor, department 
where instructor.dept name= department.dept name;

[ GROUP BY < 列名 1> [ HAVING < 条件表达式 > ] ] 
[ ORDER BY < 列名 2> [ ASC|DESC ] ] ；

select DISTINCT ISLOWER(Sdept); 系名小写, 不重复
select Sname NAME; 列别名

常用查询条件
NOT/(NOT)BETWEEN AND / (NOT))IN / (NOT))LIKE / IS (NOT) NULL
AND / OR / NOT
WHERE Sname LIKE ‘刘%’；
WHERE Sname LIKE '欧阳_'；
WHERE Cname LIKE 'DB\_%i_ _' 以DB_开头，倒数第三个字母为i
WHERE Grade IS NULL

AND 的优先级高于 OR

ORDER BY 子句  
可以按一个或多个属性列排序  
升序： ASC ；降序： DESC ；缺省值为升序
ORDER BY Grade DESC ；
ORDER BY Sdept ， Sage DESC ；

COUNT （ [DISTINCT|ALL] * ） 
COUNT （ [DISTINCT|ALL] < 列名 > ）
SUM （ [DISTINCT|ALL] < 列名 > ）
AVG （ [DISTINCT|ALL] < 列名 > ）
MAX （ [DISTINCT|ALL] < 列名 > ） 
MIN （ [DISTINCT|ALL] < 列名 > ）

SELECT Sno
FROM SC
GROUP BY Sno 
HAVING COUNT(*) >3 ； # 选修3门以上课程

HAVING 短语与 WHERE 子句的区别：
    WHERE 子句作用于基表或视图，从中选择满足条件的元组
    HAVING 短语作用于组，从中选择满足条件的组。

[GROUP BY < 列名 1> 
[HAVING < 条件表达式 >]] 
[ORDER BY < 列名 2> [ASC|DESC]

```

**SELECT 子句的 < 目标列表达式 > 可以为：**  算术表达式 / 字符串常量/  函数 / 列别名



### Query：连接查询

```sql
[< 表名 1>.]< 列名 1> < 比较运算符 > [< 表名 2>.]< 列名 2> 
[< 表名 1>.]< 列名 1> BETWEEN [< 表名 2>.]< 列名 2> AND [< 表名 2>.]< 列名 3>

嵌套循环法 (NESTED-LOOP)
查询张老师所带学生的成绩：
select *
from score
where Cno=(select Cno
           from course
           where tno=(select tno 
                      from teacher
                      where tname="张老师"
                      )    
          )


等值连接equijoin：连接运算符为 =
查询每个学生及其选修课程的情况 
SELECT Student.* ， SC.* 
FROM Student ， SC 
WHERE Student.Sno = SC.Sno ；

natural join:
SELECT Student.Sno ， Sname ， Ssex ， Sage ， Sdept ， Cno ， Grade FROM Student ， SC 
WHERE Student.Sno = SC.Sno ；

自身连接：一个表与其自己进行连接；
  - 需要给表起别名以示区别 
  - 由于所有属性名都是同名属性，因此必须使用别名前缀
查询每一门课的间接先修课（即先修课的先修课） 
SELECT FIRST.Cno ， SECOND.Cpno 
FROM Course FIRST ， Course SECOND 
WHERE FIRST.Cpno = SECOND.Cno ；

外连接与普通连接的区别
普通连接操作只输出满足连接条件的元组 
外连接操作以指定表为连接主体，将主体表中不满足连接条件的 元组一并输出
SELECT Student.Sno ， Sname ， Ssex ， Sage ， Sdept ， Cno ， Grade FROM Student LEFT OUT 
JOIN SC ON (Student.Sno=SC.Sno) ；

复合条件连接： WHERE 子句中含多个连接条件
SELECT Student.Sno, Sname 
FROM Student, SC 
WHERE Student.Sno = SC.Sno AND  /* 连接谓词 */ 
               SC.Cno= ‘2’ AND SC.Grade > 90 ； /* 其他限定条件 */

查询每个学生的学号、姓名、选修的课程名及成绩             
SELECT Student.Sno ， Sname ， Cname ， Grade 
FROM Student ， SC ， Course /* 多表连接 */ 
WHERE Student.Sno = SC.Sno and SC.Cno = Course.Cno ；

带有IN的子查询
SELECT Sno ， Sname ， Sdept 
FROM Student 
WHERE Sdept IN
		(SELECT Sdept
		FROM Student
		WHERE Sname=‘刘晨’)；
		
用自身连接完成⬆️查询
SELECT S1.Sno ， S1.Sname ， S1.Sdept 
FROM Student S1 ， Student S2 
WHERE S1.Sdept = S2.Sdept AND S2.Sname ='刘晨'；

查询选修了课程名为“信息系统”的学生学号和姓名
SELECT Sno ， Sname ③ 最后在 Student 关系中 
FROM Student 取出 Sno 和 Sname 
WHERE Sno IN (SELECT Sno ② 然后在 SC 关系中找出选 
              FROM SC 修了 3 号课程的学生学号 
              WHERE Cno IN (SELECT Cno ①首先在Course关系中找出3号                                   
                            FROM Course “ 信息系统”的课程号，为
                            WHERE Cname= ‘ 信息系统’
        										)
							);
用自身连接表达：
SELECT Sno ， Sname
FROM Student ， SC ， Course 
WHERE Student.Sno = SC.Sno AND
					SC.Cno = Course.Cno AND
					Course.Cname=‘ 信息系统’；
					
假设一个学生只可能在一个系学习，并且必须属于一个 系，则在 [ 例 39] 可以用 = 代替 IN ：
SELECT Sno ， Sname ， Sdept 
FROM Student 
WHERE Sdept =(SELECT Sdept 
              FROM Student 
              WHERE Sname=‘刘晨’)；
              
带有 ANY （ SOME ）或 ALL 谓词的子查询：
查询其他系中比计算机科学某一学生年龄小的学生 姓名和年龄
SELECT Sname ， Sage 
FROM Student 
WHERE Sage < ANY (SELECT Sage /*or select MAX(Sage)*/
                  FROM Student 
                  WHERE Sdept='CS')
             AND Sdept<>'CS';

带有 EXISTS 谓词的子查询:
  - 带有 EXISTS 谓词的子查询不返回任何数据，只产生逻辑真 值“ true” 或逻辑假值“ false” 。
  		- 若内层查询结果非空，则外层的 WHERE 子句返回真值
  		- 若内层查询结果为空，则外层的 WHERE 子句返回假值
  - 由 EXISTS 引出的子查询，其目标列表达式通常都用 * ，因 为带 EXISTS 的子查询只返回真值或假值，给出列名无实际 意义
查询所有选修了 1 号课程的学生姓名:
SELECT Sname 
FROM Student 
WHERE EXISTS
			(SELECT * 
       FROM SC 
       WHERE Sno=Student.Sno AND Cno='1')；
                
不同形式的查询间的替换:
  - 一些带 EXISTS 或 NOT EXISTS的子查询不能被其他形式的子查询等价替换
  - 所有带 IN 谓词、比较运算符、ANY 和 ALL 谓词的子查询都能用带EXISTS 谓词的子查询等价替换
  
用 EXISTS/NOT EXISTS 实现全称量词 /*( 难点 ) */
  -SQL 语言中没有全称量词（ For all ） 可以把带有全称量词的谓词转换为等价的带有存在量词的谓词：(all x)P ≡ 非(ex. x(非P))

查询与“刘晨”在同一个系学习的学生。 可以用带 EXISTS 谓词的子查询替换： SELECT Sno ， Sname ， Sdept 
FROM Student S1 
WHERE EXISTS 　 
		(SELECT * 
     FROM Student S2 
     WHERE S2.Sdept = S1.Sdept AND S2.Sname = ‘ 刘晨’ ) ；
     
查询选修了全部课程的学生： 
SELECT Sname  
FROM Student
WHERE NOT EXISTS  /*对a，所有课程都不存在有一门x没被选*/
		(SELECT *
     FROM Course
     WHERE NOT EXISTS  /*不存在学生a选了课程x，即a没选x*/
     			(SELECT *  
           FROM SC
           WHERE Sno=Student.Sno  
           	 AND Cno=Course.Cno
          )
    );
    
用 EXISTS/NOT EXISTS 实现逻辑蕴函 /*( 难点 )*/
  - SQL 语言中没有蕴函 (Implication) 逻辑运算
  - 可以利用谓词演算将逻辑蕴函谓词等价转换 p➡️q ≡ 非p∨q
查询至少选修了学生 200215122 选修的全部课程的 学生号码。
解题思路：
用逻辑蕴函表达：查询学号为 x 的学生，对所有的课程 y ，只 要 200215122 学生选修了课程 y ，则 x 也选修了 y 。 形式化表示： 
用 P 表示谓词 “学生 200215122 选修了课程 y” 
用 q 表示谓词 “学生 x 选修了课程 y”
```

![](https://tva1.sinaimg.cn/large/0082zybpgy1gbvokjnhklj30o409kab0.jpg)

```sql
转换后的语义： 不存在这样的课程 y ，学生 200215122 选 修了 y ，而学生 x 没有选。
用 NOT EXISTS 谓词表示：
SELECT DISTINCT Sno 
FROM SC SCX 
WHERE NOT EXISTS
			(SELECT *
       FROM SC SCY
       WHERE SCY.Sno = ' 200215122 ' 
       AND NOT EXISTS (  /*不存在z选了x，y的课*/
        	  SELECT * 
          	FROM SC SCZ 
         		WHERE SCZ.Sno=SCX.Sno AND SCZ.Cno=SCY.Cno)) ；
         		
集合查询： UNION， INTERESECT， EXCEPT
  - 参加集合操作的各查询结果的列数必须相同；对 应项的数据类型也必须相同
查询计算机科学系的学生及年龄不大于 19 岁的学生。：
SELECT * 
FROM Student 
WHERE Sdept= 'CS' 
UNION 
SELECT * 
FROM Student 
WHERE Sage<=19 ；

法2:
SELECT DISTINCT * 
FROM Student 
WHERE Sdept= 'CS' OR Sage<=19 ；

查询计算机科学系的学生与年龄不大于 19 岁的学生的交集：
SELECT * 
FROM Student 
WHERE Sdept='CS' 
INTERSECT 
SELECT * FROM Student WHERE Sage<=19

即
SELECT * FROM Student WHERE Sdept= 'CS' AND Sage<=19 ；


```



### 数据更新

```sql
插入数据
INSERT 
INTO < 表名 > [(< 属性列 1>[ ， < 属性列 2 >…)] 
VALUES (< 常量 1> [ ， < 常量 2>] … )
              
ie.
INSERT 
INTO Student (Sno ， Sname ， Ssex ， Sdept ， Sage) 
VALUES ('200215128' ， ' 陈冬 ' ， ' 男 ' ， 'IS' ， 18) ；
              
插入子查询结果
INSERT 
INTO < 表名 > [(< 属性列 1> [ ， < 属性列 2>… )]
子查询；
              
修改数据
UPDATE < 表名 >
SET < 列名 >=< 表达式 >[ ， < 列名 >=< 表达式 >]… 
[WHERE < 条件 >] ； /*修改指定表中满足 WHERE 子句条件的元组*/
              
三种修改方式
1. 修改某一个元组的值
2. 修改多个元组的值
3. 带子查询的修改语句   
              
UPDATE Student 
SET Sage= Sage+1 ； 
              
将计算机科学系全体学生的成绩置零。

UPDATE SC 
SET Grade=0 
WHERE 'CS'=
		(SELETE Sdept
		FROM Student
		WHERE Student.Sno = SC.Sno) ；              
              
删除数据：
DELETE
FROM < 表名 > 
[WHERE < 条件 >]             


```



### 视图

```sql
CREATE VIEW 
	< 视图名 > [(< 列名 > [ ， < 列名 >]…)] 
AS < 子查询 > 
[WITH CHECK OPTION] ；

  - 子查询不允许含有 ORDER BY 子句和 DISTINCT 短语
  
建立信息系学生的视图。
CREATE VIEW IS_Student 
AS 
SELECT Sno ， Sname ， Sage 
FROM Student 
WHERE Sdept= 'IS' ；

建立信息系选修了 1 号课程的学生视图。
CREATE VIEW IS_S1(Sno ， Sname ， Grade) 
AS 
SELECT Student.Sno ， Sname ， Grade 
FROM Student ， SC 
WHERE Sdept= 'IS' AND Student.Sno=SC.Sno AND SC.Cno= '1' ；

...ppt3-5



```



























