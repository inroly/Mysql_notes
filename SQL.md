

#SQL 学习笔记

---
##SQL语法规范

假设一个Person表

 id|LastName            | FirstName        |   Adress       |
---|--------------------|------------------|-------------   |
1  | Adams              | John             | Oxford Street  |
2  | Bush               | George           | Fifth Avenue   |
3  | Carter             | Thomas           | Changan Street |

从表中选取LastName行

SELECT LastName FROM Persons

LastName|
--------|
Adams   |
Bush    |
Carter  |

***important notice***

*SQL语句大小写不敏感*

*但是约定大小写*

---
**SQL 语句后面的分号？**

某些数据库系统要求在每条 SQL 命令的末端使用分号。在我们的教程中不使用分号。

分号是在数据库系统中分隔每条 SQL 语句的标准方法，这样就可以在对服务器的相同请求中执行一条以上的语句。

如果您使用的是 MS Access 和 SQL Server 2000，则不必在每条 SQL 语句之后使用分号，不过某些数据库软件要求必须使用分号。

---
**SQL DML 和 DDL**
可以把 SQL 分为两个部分：数据操作语言 (DML) 和 数据定义语言 (DDL)。
SQL (结构化查询语言)是用于执行查询的语法。但是 SQL 语言也包含用于更新、插入和删除记录的语法。

查询和更新指令构成了 SQL 的 DML 部分：

+ SELECT - 从数据库表中获取数据
+ UPDATE - 更新数据库表中的数据
+ DELETE - 从数据库表中删除数据
+ INSERT INTO - 向数据库表中插入数据


SQL 的数据定义语言 (DDL) 部分使我们有能力创建或删除表格。我们也可以定义索引（键），规定表之间的链接，以及施加表间的约束。

SQL 中最重要的 DDL 语句:

- CREATE DATABASE - 创建新数据库
- ALTER DATABASE - 修改数据库
- CREATE TABLE - 创建新表
- ALTER TABLE - 变更（改变）数据库表
- DROP TABLE - 删除表
- CREATE INDEX - 创建索引（搜索键）
- DROP INDEX - 删除索引


 **inportant tips**
 
 - 关键字函数名全部大写
 - 数据库名称、表名称、字段名称全部小写
 - SQl语句必须以分号结尾
 
 ---

##DATABASE 操作
 


`SHOW DATABASES;`

展示数据库

`SHOW WARNINGS;`

展示warning

`SHOW CREATE DATABASE test;`

展示创建数据库的命令

--

*其中{}为必填  []为选填*

```
CREATE {DATABASE| SCHEMA} [IF NOT EXISTS] db_name [DEFAULT] CHARACTER SET [=] charset_name;
```

创建数据库的命令

`CREATE DATABASE test;`

创建名为test数据库

`CREATE DATABASE IF NOT EXISTS test;`

创建名为test的数据库，如果存在则创建，不存在则抛出warning


--


```
ALTER {DATABASE| SCHEMA} [IF NOT EXISTS] db_name [DEFAULT] CHARACTER SET [=] charset_name;
```

`ALTER DATABASE test CHARACTER SET = utf8;`

更新test数据库，将编码转换为 utf8

--

```
DROP {DATABASE| SCHEMA} [IF NOT EXISTS] db_name;
```

`DROP DATABASE test;`

删除名为test的数据库

--

`USE db_name;`

打开数据库

---

##数据表操作

```
CREAT TABLE [IF NOT EXISTS] table_name(column_name data_type, ...);
```
创建数据表，()内为列信息

```
test>CREATE TABLE testtable(
    -> username VARCHAR(20) NOT NULL,
    -> age TINYINT,
    -> pay FLOAT(8,2) UNSIGNED
    -> );
```
NOT NULL表示非空，空会报错，usigned为无符号，负值报错。
```
test>CREATE TABLE testtable(
    -> id SMALLINT UNSIGNED AUTO_INCREMENT,
    -> age TINYINT,
    -> pay FLOAT(8,2) UNSIGNED
    -> );
```
AUTO_INCREMENT 为自动编号，默认情况下起始值为1，每次增量为1
*example*

--
```
CREATE TABLE testtable(
	-> id SMALLINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
	-> age TINYINT,
	-> pay FLOAT(8,2) UNSIGNED
	-> );
```
主键约束
每张数据表只能存在一个主键
主键保证记录的唯一性
主键自动为NOT NULL
```
SHOW TABLES [FROM db_name] [LINK 'pattern' |WHERE expr];
```
展示数据库中的数据表

```
SHOW COLUMNS FROM tbl_name;
```
展示数据表中的列信息

--

```
INSERT [INTO] tbl_name[(col_name,...)] VALUES(val,...);
```
INSERT testtable(username,age) VALUES('Matthew',25);

*example*



 