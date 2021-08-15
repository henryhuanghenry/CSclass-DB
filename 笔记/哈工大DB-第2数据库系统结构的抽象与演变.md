# 哈工大DB-第二讲数据库系统结构的抽象与演变

[TOC]



## 0.本讲学什么

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815141616900.png" alt="image-20210815141616900" style="zoom:50%;" />

## 1.数据库系统的标准结构? 

### 1.1DBMS管理数据的三个层次

- 用户层次 External Level     =  User Level 
  - 某一用户能够看到与处理的数据,   全局数据中的某一部分
- 逻辑层次 Conceptual Level     =  Logic level
  - 从全局角度理解/管理的数据, 含相应的关联约束
- 物理层次 Internal Level     =  Physical level
- 存储在介质上的数据，含存储路径、存储方式 、索引方式等

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815142108956.png" alt="image-20210815142108956" style="zoom:50%;" />

### 1.2数据模式与视图

- 模式(Schema) --一种抽象的结构

  - 对数据库中数据所进行的一种**结构性的描述**所观察到数据的**结构信息**

- 视图(View)/数据(Data)--在抽象的结构规定下的真实数据

  - 某一种**表现形式**下表现出来的数据库中的**数据**

  <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815142319718.png" alt="image-20210815142319718" style="zoom:50%;" />

### 1.3三级模式与两层映象

**三级模式：**

- External Schema   ---- (External) View
  - 某一**用户能够看到**与处理的数据的结构描述
- (Conceptual) Schema     ---- Conceptual View
  - 从**全局角度理解/管理的数据的结构描述**, 含相应的**关联约束**体现在**数据之间的内在本质联系**
- Internal Schema     ---- Internal  View
  - **存储在介质上的数据的结构描述**，含存储路径、存储方式 、索引方式等

**两层映象：** 以概念模式为基础，向外映射为外模式方便用户使用，想内映射为内模式方便计算机存储

- E-C Mapping：External Schema-Conceptual Schema Mapping 
  - 将概念模式映射为外模式，从而支持实现数据概念视图向外部视图的转换
  - 便于用户观察和使用
- C-I Mapping：Conceptual Schema-Internal Schema Mapping 
  - 将概念模式映射为内模式，从而支持实现数据概念视图向内部视图的转换
  - 便于计算机进行存储和处理

### 1.4两个独立性--按照标准结构抽象数据库的原因

- **逻辑数据独立性**--逻辑模式变而不影响用户模型
  - 当概念模式变化时，可以不改变外部模式(只需改变E-C Mapping)，从而无需改变应用程序
- **物理数据独立性**--内部模式变而不影响概念模型
  - 当内部模式变化时，可以不改变概念模式(只需改变C-I Mapping) ，从而不改变外部模式

## 2. 数据模型? 

### 2.1模型与模式

- <font color=blue>数据模型--**对模式的抽象**</font>
  - **规定模式统一描述方式的模型**，包括：数据结构、操作和约束
  - **数据模型是对模式本身结构的抽象**
- <font color=blue>模式--对**数据本身结构形式**的抽象</font>
- 比如：关系模型
  - 所有模式都可为抽象表(Table)的形式[数据结构]
  - 每一个具体的模式都是拥有不同列名的具体的表。对这种表形式的数据有哪些[操作]和[约束]
- 个人理解，模型是规定了一个数据库的数据结构、操作和约束。而模式是在模型的规定下，针对不同的数据有着不同的范式。

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815143820533.png" alt="image-20210815143820533" style="zoom:67%;" />

### 2.2三大经典数据模型
- **关系模型**：**表**的形式组织数据
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815143845208.png" alt="image-20210815143845208" style="zoom:50%;" />
- **层次模型**：**树**的形式组织数据
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815143939461.png" alt="image-20210815143939461" style="zoom:50%;" />
- **网状模型**：**图**的形式组织数据
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815144015264.png" alt="image-20210815144015264" style="zoom:50%;" />

## 3. 数据库系统的演变与发展?

### 3.1简要发展史

- 第一阶段：数据库技术探索阶段(59-65/67)
  - 研制成功**格式文件系统**
  - 正式提出“Data Base”，并开始进行研究
- 第二阶段：数据库技术确立阶段(65/68-75)
  - 三大数据库：层次、网状及关系数据库相继提出并进行了深入研究
  - 商用数据库出现并应用，但多为网状及层次型系统
  - **数据库研究形成理论基础：关系数据库理论**
- 第三阶段：数据库技术成熟阶段(76-80s前期)
  - 提出了**标准化数据库系统结构模型**
  - 关系DB系统迅速发展：如SQL, QBE, System R ,Ingres等
  - 关系理论日臻完善，包括规范化理论，关系语言，RDB的设计与实现，新型关系模型等；
  - 数据库应用已十分普及，渗透到社会各个方面，出现众多DB的技术分支，DB走向全面成熟，人称70年代为“数据库的年代”
- 第四阶段：数据库技术深化发展阶段(85年以来)
  - 数据库方法逐步理论化、数据库设计理论不断完善
  - **新型数据模型、专用数据模型**, 专用型、新型数据库系统，不断涌现
  - 数据库技术+其他计算机技术结合 == 面向各行各业的专用数据库

### 3.2重要发展阶段

#### 从 文件系统 到 数据库

- 文件系统的缺点：数据的组织依赖于应用程序，如果想要数据的组织结构发生变化则需要修改应用程序
- 使用数据库系统可以统一存储以及维护数据的组织形式，使得数据独立于应用程序

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815145224844.png" alt="image-20210815145224844" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815145257534.png" alt="image-20210815145257534" style="zoom:50%;" />

#### 从 层次/网状模型 到 关系模型

- 层次模型与网状模型数据库
  - 数据之间的关联关系由复杂的指针系统来维系，结构描述复杂
  - **数据检索操作依赖于由指针系统指示的路径**
  - 逐一记录的操作，**不能有效支持记录集合的操作**
- 关系模型数据库
  - 数据之间的关联关系由Table中属性的值来表征，**结构描述简单**：Table/relation
  - 数据检索操作不依赖于路径信息或过程信息，支持非过程化的数据操作
  - **有效支持记录集合的操作**
  - 较为完善的理论基础

#### 从 关系模型数据库 到 对象关系模型/面向对象数据库 

- 关系数据库
  - **按行按列形式组织数据**：**关系的第1范式**
  - **数据项的不可再分特性**
  - 关系运算: 关系代数、元组演算、域演算--标准SQL
  - 关系数据库设计理论
- 对象-关系数据库
  - 可有效支持不满足关系第1范式的数据项
  - 以对象来封装需分解的数据项
  - 行对象与列对象；**聚集对象与结构对象**
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815145837873.png" alt="image-20210815145837873" style="zoom:50%;" />
- 面向对象数据库
  - 面向对象技术(O-O)与集合/聚集操作技术(SQL)的结合
  - 支持复杂的数据类型，数据封装与抽象数据结构
  - 支持面向对象的一些特性：类、继承、封装、多态…
- XML数据库
  - 是数据库的另一种形式, 被称为半结构化数据库;
  - 数据 与 数据的语义 合并在一起进行存储和处理;
  - 面向数据交换而提出, 在互联网世界得到广泛应用
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815145930209.png" alt="image-20210815145930209" style="zoom:50%;" />

#### 从 普通数据库 到 新型数据库

- 普通
  - Oracle
  - Sybase
  - Ingres
  - DB 2
  - MS Access
  - Informix
- 开放互联数据库
  - ODBC
  - JDBC
- 新型数据库
  - OA：DB + Management Information System
  - Database Machine  DB + Computer Architecture
  - Intelligent Database  DB + Artificial Intelligence
  - Distributed Database(DDB)  DB + Computer Network。
  - Image Database / Multimedia Database  DB + Image processing / Multimedia processing。
  - Temporal Database  DB + 时态技术处理。
  - Mobile Database  DB + 移动计算技术。
  - Active Database  DB + 产生式规则/触发器技术。
  - Fuzzy Database  DB + 模糊处理技术。
  - Real-Time Database  DB + 实时处理技术。
  - Engineering Database  DB + CAD/CAPP/CAM技术。
  - Geographical Databas和空间数据库(Spacial Database)  DB + 数字地图、全球定位、空间分析技术。
  - Statistical Database  DB + 统计学。
  - Internet Database  DB + Internet/WWW(网页/HTML文档)。
  - Data Warehouse/Data Mining  DB + OLAP + 统计学。
  - NoSQL

## 4.小结

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\笔记\${图片}\image-20210815150131446.png" alt="image-20210815150131446" style="zoom:50%;" />