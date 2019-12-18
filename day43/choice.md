### 1. 一个关系数据库文件中的各条记录（）
- [ ] A. 前后顺序不能任意颠倒，一定要按照输入的顺序排列
- [x] B. 前后顺序可以任意颠倒，不影响库中的数据关系
- [ ] C. 前后顺序可以任意颠倒，但排列顺序不同，统计处理的结果就可能不同
- [ ] D. 前后顺序不能任意颠倒，一定要按照关键字字段值的顺序排列

### 2. 一名员工可以使用多台计算机，每台计算机只能由一名员工使用，则实体员工和计算机间的联系是（）
- [x] A. 一对多
- [ ] B. 多对多
- [ ] C. 多对一
- [ ] D. 一对一

### 3. 下列关于视图的说法错误的是（）
- [ ] A. 视图是从一个或多个基本表导出的表，它是虚表
- [x] B. 视图一经定义就可以和基本表一样被查询、删除和更新
- [ ] C. 某一用户可以定义若干个视图
- [ ] D. 视图可以用来定义新的视图

### 4. 订单表（订单号，雇员代号，地区代号，订购日期）中订单号为主键，要删除订单中前三年以前的信息，SQL 为（）
- [ ] A. delete from 订单表 where 订购日期<getdate()+3
- [ ] B. delete from 订单表 where 订购日期<DATEADD(yy,3,getdate())
- [ ] C. delete from 订单表 where 订购日期<getdate()-3
- [x] D. delete from 订单表 where 订购日期<DATEADD(yy,-3,getdate())

### 5. 负责数据库中查询操作的数据库语言是（）
- [ ] A. 数据定义语言
- [ ] B. 数据管理语言
- [x] C. 数据操纵语言
- [ ] D. 数据控制语言

### 6. 数据库管理系统是（）
- [ ] A. 操作系统的一部分
- [x] B. 在操作系统支持下的系统软件
- [ ] C. 一种编译系统
- [ ] D. 一种操作系统

### 7. SQL 语句中修改表结构的命令是（）
- [ ] A. MODIFY TABLE
- [ ] B. MODIFY STRUCTURE
- [x] C. ALTER TABLE
- [ ] D. ALTER STRUCTURE

### 8. 在 SQL 数据库中，哪个语句能校验整数列 i 的值不小于 1 不大于 10（）
- [x] A. i BETWEEN 1 AND 10
- [ ] B. i BETWEEN 0 AND 11
- [ ] C. i IN INTERVAL(0,11)
- [ ] D. i IN INTERVAL(1,10)

### 9. 在学生表 Student 的系别 (Sdept) 属性中查询信息系 (IS) 、数学系 (MA) 和计算机系 (CS) 的学生姓名 (Sname) 和性别 (Ssex) ，正确的命名格式应为（）
- [ ] A. SELECT Student FROM Sname, Ssex WHERE Sdept IN (‘IS’, ’MA’, ‘CS’)
- [x] B. SELECT Sname, Ssex FROM Student WHERE Sdept IN (‘IS’, ’MA’, ‘CS’)
- [ ] C. SELECT Sname, Ssex FROM Student WHERE Sdept (IS, MA, CS)
- [ ] D. SELECT Sname, Ssex FROM Student WHERE Sdept LIKE IS, MA, CS

### 10. SQL 查询语句中 WHERE、GROUP BY、HAVING 这些关键字区别和用法总结错误的是（）
- [ ] A. HAVING 在查询语句中必须依赖于 GROUP BY
- [ ] B. WHERE 子句用来限制 SELECT 语句从表中指定选取的行
- [ ] C. GROUP BY 子句用来分组 WHERE 子句的输出结果集
- [x] D. HAVING 子句用来从分组的结果中筛选列
