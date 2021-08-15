# 哈工大DB-第一讲初步认识数据库

[TOC]



## 0.数据库系统学什么

### 0.1数据库课程的知识点

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815135008471.png" alt="image-20210815135008471" style="zoom:50%;" />

### 0.2数据库课程的划分

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815135107866.png" alt="image-20210815135107866" style="zoom:50%;" />

### 0.3数据库课程与其他课程的联系

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815135149916.png" alt="image-20210815135149916" style="zoom:50%;" />

## 1.什么是数据库

### 1.1数据库是电子化信息的集合

- 将信息规范化并使之电子化,形成电子信息 ‘库’,以便利用计算机对这些信息进行快速 有效的存储、检索、统计与管理
- Collection of related data 
- Storage place for data  
- Get Information from 

### 1.2数据库与表

- 数据库起源于规范化“表(Table)”的处理 
- Table: 以按行按列形式组织及展现的数据

### 1.3表的构成

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815135821806.png" alt="image-20210815135821806" style="zoom:50%;" />

### 1.4数据库与表的关系

Database: 相互之间有关联关系的Table的集合

## 2.什么是数据库系统

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815140145255.png" alt="image-20210815140145255" style="zoom:50%;" />

## 3.什么是数据库管理系统

### 3.1从用户角度看数据库管理系统的功能

- **数据库定义:** 定义数据库中Table的名称、标题(内含的属性名称及对该 属性的值的要求)等  
  - DBMS提供一套**数据定义语言(DDL:Data Definition Language)**给用户
  - 用户使用DDL描述其所要建立表的格式 
  - DBMS依照用户的定义，创建数据库及其中的Table
- **数据库操纵:** 向数据库的Table中增加/删除/更新数据及对数据进行查 询、检索、统计等
  - DBMS提供一套**数据操纵语言(DML:Data Manipulation Language)**给用户
  - 用户使用DML描述其所要进行的增、删、改、查等操作
  - DBMS依照用户的操作描述，实际执行这些操作
- **数据库控制:** 控制数据库中数据的使用---哪些用户可以使用,哪些不可以
  - DBMS提供一套**数据控制语言(DCL:Data Control Language)**给用户
  - 用户使用DCL描述其对数据库所要实施的控制
  - DBMS依照用户的描述，实际进行控制
- **数据库维护:** 转储/恢复/重组/性能监测/分析… 
  - DBMS提供一系列程序(实用程序/例行程序) 给用户
  - 在这些程序中提供了对数据库维护的各种功能
  - 用户使用这些程序进行各种数据库维护操作
- 数据库维护的实用程序，一般都是由数据库管理员(DBA)来使用和掌握
- 数据库语言：使用者通过数据库语言利用DBMS操作数据库
  - 数据定义语言(DDL:Data Definition Language) ----DBMS提供给用户,以便用户定义数据格式 
  - 数据操纵语言(DML:Data Manipulation Language) ----DBMS提供给用户,以便用户对数据进行操作 
  - 数据控制语言(DCL:Data Control Language) ----DBMS提供给用户,以便用户对数据进行控制 
  - 数据库各种操作的执行 ----DBMS按用户要求进行定义、操纵、控制和维护
- SQL语言：结构化 的数据库语言（数据库语言可以嵌入到高级语言(宿主语言)中使用）

### 3.2从系统实现角度看DBMS的功能

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815141005377.png" alt="image-20210815141005377" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815141036298.png" alt="image-20210815141036298" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815141054993.png" alt="image-20210815141054993" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815141123097.png" alt="image-20210815141123097" style="zoom:50%;" />

### 3.3小结

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815141201810.png" alt="image-20210815141201810" style="zoom:50%;" />
