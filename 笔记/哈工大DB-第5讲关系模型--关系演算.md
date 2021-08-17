# 哈工大DB-第5讲关系模型--关系演算



## 0.本讲学什么

1. 关系演算之关系元组演算
2. 关系演算之关系域演算
3. 关系演算之安全性
4. 关于三种关系运算的一些观点

重点与难点：

- 关系元组演算公式的递归定义；关系域演算公式的递归定义
- 关系元组演算公式：与 $\and$、或$\or$、非$\lnot$、存在量词$\exists$、全称量词$\forall$
- 用关系元组演算公式表达查询的思维训练
- 用QBE语言表达查询的思维训练
- 关系元组演算、域演算和关系代数在表达查询方面的思维差异



## 1.关系元组演算

### 1.1 概述

#### 1.1.1 概述

关系演算是以数理逻辑中的**谓词演算**为基础的

- 关系演算是描述关系运算的另一种思维方式
- SQL语言是继承了关系代数和关系演算各自的优点所形成的
- 按照谓词变量的不同，可分为**关系元组演算**和**关系域演算**
  - **关系元组演算**是以**元组变量**作为谓词变量的基本对象
  - **关系域演算**是以**域变量**作为谓词变量的基本对象

#### 1.1.2关系元组演算公式的形式

- 关系元组演算公式的基本形式：$\{ t | P(t) \}$​
- 上式表示：**所有使谓词 P 为真的元组 t 的集合**
- t 是元组变量
- $t\in r$​ 表示元组 t 在关系 r 中
- t [A] 表示元组 t 的分量，即 **t 在属性 A 上的值**
- P 是与谓词逻辑相似的公式, P(t)表示以元组 t 为变量的公式
- P(t)可以递归地进行定义

#### 1.1.3 关系元组演算公式的完整定义

- 关系元组演算公式的基本形式：$\{ t | P(t) \}$
- 其中公式P(t)可以递归地进行构造：
  - 三种形式的**原子公式**是公式
    - $s \in R$
    - $s[A]\theta c$​ （c是常量, s[A]是s上的A分量）
    - $s[A]\theta u[B]$
  - 如果$P$是公式，那么$\lnot P$也是公式
  - 如果P1 , P2是公式，则$P1\and P2$, $P1\or P2$也是公式
  - 如果P(t)是公式，R是关系，则$\exists(t\in R)(P(t))$和$\forall(t\in R)(P(t))$也是公式
  - 需要时可加括弧
  - 上述运算符的**优先次序**自高至低为：括弧；$\exists$；$\forall$；$\lnot$；$\and$；$\or$
  - **公式只限于以上形式**

### 1.2 原子公式及与、或、非之理解与运用

#### 1.2.1 原子公式--属于、分量与常量比较、分量与分量比较

- $t \in R$
  - **t 是关系 R 中的一个元组**，例如： { t | t ∈ Student }
- $s[A]\theta c$​​ （c是常量, s[A]是s上的A分量）
  - **元组分量s[A]**与**常量 c** 之间满足比较关系$\theta$​​($>,<,=,<>,\leq,\geq$​)
  -  $\{ t | t\in R \and t [Sage ] <= 19 \and t [Sname ] = '张三' \}$​
- $s[A]\theta u[B]$​
  - s[A] 与 u[B] 为元组分量，A和B分别是某些关系的属性，他们之间满足比较关系$\theta$​.
  - 例如： $\{ t | t\in Student \and \exist (u\in Student) ( t [Sage ] > u [Sage ] ) \}$“检索出年龄不是最小的所有同学”

#### 1.2.2 与、或、非运算符--连接公式

- P(t)可以由公式加运算符 $\lnot$；$\and$；$\or$​递归地构造
- 如果F是一个公式，则 $\lnot$ 也是公式
- 如果F1、F2是公式，则 F1$\and$F2, F1$\or$​F2也是公式
- 运算符的**优先次序**自高至低为：括弧；$\exists$；$\forall$；$\lnot$；$\and$；$\or$​

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817105403870.png" alt="image-20210817105403870" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817105422970.png" alt="image-20210817105422970" style="zoom:50%;" />

### 1.3 存在量词与全称量词之理解与运用

- 构造P(t)还有两个运算符： $\exists$（存在)、$\forall$  (任意)
- 如果P(t)是公式，R是关系，则$\exists(t\in R)(P(t))$和$\forall(t\in R)(P(t))$​也是公式
-  $\exists$（存在)、$\forall$  (任意)，又称为量词，前者称“存在量词”，后者称“全称量词”
- 而被 $\exists$（存在)、$\forall$​​​  (任意)限定的元组变量 t , 或者说，元组变量 t 前有存在量词或全称量词，则该变量被称为**“约束变量”**，否则被称为“自由变量”。
- **这些量词主要是对t进行验证，验证这个t是否满足条件，满足条件才留下**

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817110013625.png" alt="image-20210817110013625" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817110038346.png" alt="image-20210817110038346" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817110101873.png" alt="image-20210817110101873" style="zoom:50%;" />

上图练习：课程学了都及格的同学的学号$\prod_{S\#}(SC)-\prod_{S\#}(\sigma_{Score<60}(SC))$​

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817110119946.png" alt="image-20210817110119946" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817110145077.png" alt="image-20210817110145077" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817110204073.png" alt="image-20210817110204073" style="zoom:50%;" />

### 1.4 应用训练语义正确性与等价性变换训练

#### 1.4.1 等价性变换

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817114527903.png" alt="image-20210817114527903" style="zoom:67%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817114549168.png" alt="image-20210817114549168" style="zoom: 50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817114642066.png" alt="image-20210817114642066" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817114615942.png" alt="image-20210817114615942" style="zoom:50%;" />

#### 1.4.2 四个复杂例子

##### 全都--全称内嵌存在

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817115010210.png" alt="image-20210817115010210" style="zoom:50%;" />

##### 全都没--全称内嵌不存在

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817115026163.png" alt="image-20210817115026163" style="zoom:50%;" />

##### 至少有一--存在内嵌存在

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817115042245.png" alt="image-20210817115042245" style="zoom:50%;" />

##### 至少有一没--存在内嵌不存在

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817115059287.png" alt="image-20210817115059287" style="zoom:50%;" />



#### 1.4.3 将关系代数转换为元组演算

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817115134627.png" alt="image-20210817115134627" style="zoom:67%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817115203842.png" alt="image-20210817115203842" style="zoom: 80%;" />

### 1.5 书写总结

- 要输出/要操作的表，都要设置一个元组，以便操作。一个表甚至能有多个元组
- 存在或者全称量词，第一个括号要限制检验的范围，第二个括号设置检验的条件
- 存在，即检验范围内有满足条件的元组，使得检验的结果为真
- 全称，即检验范围内的所有元组都必须满足条件，检验结果才为真
- 需要牢记的是，存在或者全称其实都是一个真假语句，利用**与或非真假**的思想，不要被复杂的条件迷惑



## 2.关系域演算

#### 2.1关系域演算的定义

- 关系域演算公式的基本形式： { < x1 , x2 , … , xn > | P ( x1 , x2 , … , xn ) }
- 其中， xi 代表域变量或常量， P为以xi为变量的公式。
- 公式P可以递归地进行构造：
  - 三种形式的原子公式是公式
    - $< x1 , x2 , … , xn > \in R$​。 其中**xi 代表域变量或常量**, 表示由域变量构成的< x1 , x2 , … , xn >是属于关系R的
    - $x\theta c$。 其中，域变量x与常量c之间满足比较关系$\theta$ 。$\theta$ ：比较运算符 $<,>,<>,\leq,\geq$
    - $x\theta y$。其中，域变量x与域变量y之间满足比较关系$\theta$
  - 如果P是公式，那么$\lnot P$也是公式
  - 如果P1 , P2是公式，则$P1\and P2$​​ , $P1\or P2$​​ 也是公式
  - 如果P是公式， x是域变量，则$\exists(x)(P(x))$和$\forall(x)(P(x))$也是公式
    - 需要时可加括弧
    - 上述运算符的优先次序自高至低为：括弧；$\exists$；$\forall$；$\lnot$；$\and$；$\or$；
    - 公式只限于以上形式

#### 2.2示例

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817151421414.png" alt="image-20210817151421414" style="zoom:50%;" />

#### 2.3与元组演算的区别

- 元组演算的基本形式： { t | P(t) }
- 域演算的基本形式： { < x1 , x2 , … , xn > | P ( x1 , x2 , … , xn ) }
- **元组演算是以元组为变量**，以元组为基本处理单位，先找到元组，然后再找到元组分量，进行谓词判断；
- **域演算是以域变量为基本处理单位**，先有域变量，然后再判断由这些域变量组成的元组是否存在或是否满足谓词判断。
- 公式的运算符($\and$​​​(与)、 $\or$​​​ (或)、 $\lnot$​​​(非)、 $\forall$​​ (全称量词)和$\exist$​(存在量词))是相同的，只是其中的变量不同
- 元组演算和域演算可以等价互换。

## 3.基于关系域演算的QBE语言

#### 3.1语言概述

域演算语言QBE

- QBE: Query By Example
- 1975年由M. M. Zloof提出，1978年在IBM370上实现
- 特点：操作独特，基于屏幕表格的查询语言，不用书写复杂的公式，只需将条件填在表格中即可
- 是一种高度非过程化的查询语言
- 特别适合于终端用户的使用

#### 3.2QBE基本形式

QBE操作框架由四个部分构成

- 关系名区：用于书写欲待查询的关系名
- 属性名区：用于显示对应关系名区关系的所有属性名
- 操作命令区：用于书写查询操作的命令
- 查询条件区：用于书写查询条件
- <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817151915923.png" alt="image-20210817151915923" style="zoom:50%;" />



#### 3.3QBE的操作

- 基本操作命令

  - Print 或 P.   ---- 显示输出操作
  - Delete或D.   ---- 删除操作
  - Insert或I.     ---- 插入操作
  - Update或U. ---- 更新操作
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817152045621.png" alt="image-20210817152045621" style="zoom:50%;" />

- 查询--简单条件查询

  - QBE查询条件可以直接在查询条件区中书写，形式为 $\theta$参量
    -  $\theta$ 可以是<, >, >=, <=, =, <>; 如省略$\theta$ ，则默认为 =
    -  $\theta$​ 参量中的参量可以是常量，直接书写；
    - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817152422024.png" alt="image-20210817152422024" style="zoom:50%;" />

- 查询--不同属性上的**与条件**

  - QBE**不同属性上的与条件**可以**写在同一行中**
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817152456178.png" alt="image-20210817152456178" style="zoom:50%;" />

- 查询--示例元素与投影

  - 条件  $\theta$ 参量中的参量也可以是域变量，用任何一个值(不必是结果中的值)带有下划线表示，被称为示例元素.
  - 示例元素**下划线上面的值不起作用**，**被当作域变量名称来对待**，只用于占位或是连接条件。
  - 不带划线的则是构成实际条件一部分的值。
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817152727600.png" alt="image-20210817152727600" style="zoom:50%;" />

- 查询--用示例元素实现‘与’运算和‘或’运算

  - $\or$​条件(或运算)时，可以采用在多行书写，然后在打印命令后使用不同的示例元素来表征，如下图, 一行写为P.X, 一行使用P.Y。
    - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817152830547.png" alt="image-20210817152830547" style="zoom:50%;" />
  - $\and $条件分多行书写，则相互存在$\and $​关系的行要采用相同的示例元素
    - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817152910772.png" alt="image-20210817152910772" style="zoom:50%;" />

- 查询--相当于括号的条件表示

  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817152930805.png" alt="image-20210817152930805" style="zoom:50%;" />

- 查询--用示例元素实现多个表的连接

  - 当检索涉及多个表时，可利用**同一连接条件使用相同的示例元素**，来**实现多个表的连接**
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817153017444.png" alt="image-20210817153017444" style="zoom:50%;" />

  

### 应用训练--PPT273



## 4.关系演算的安全性

**<font color=blue>“不产生无限关系和无穷验证的运算被称为是安全的”</font>**

- <font color=blue>**关系代数是一种集合运算，是安全的**</font>
  - **集合本身是有限的，有限元素集合的有限次运算仍旧是有限的。**
- <font color=blue>**关系演算不一定是安全的**</font> 
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817161234213.png" alt="image-20210817161234213" style="zoom:50%;" />

#### 安全约束

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817161350252.png" alt="image-20210817161350252" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817161411346.png" alt="image-20210817161411346" style="zoom:50%;" />

## 5.关于关系运算的一些观点

关系运算有三种：关系代数、关系元组演算和关系域演算

- 三种关系运算都是抽象的数学运算，体现了三种不同的思维
- 关系代数---以集合为对象的操作思维，由集合到集合的变换
- 元组演算---以元组为对象的操作思维，取出关系的每一个元组进行验证，有一个元组变量则可能需要一个循环，多个元组变量则需要多个循环
- 域演算---以域变量为对象的操作思维，取出域的每一个变量进行验证看其是否满足条件

- **三种运算之间是等价的**
- 关系代数 与 安全的元组演算表达式 与 安全的域演算表达式 是等价的。即一种形式的表达式可以被等价地转换为另一种形式
- 三种关系运算都可说是**非过程性的**
  - **相比之下：域演算的非过程性最好，元组演算次之，关系代数最差**
- 三种关系运算虽是抽象的，但却是**衡量数据库语言完备性的基础**
  - **一个数据库语言如果能够等价地实现这三种关系运算的操作，则说该语言是完备的**
  - 目前多数数据库语言都能够实现这三种运算的操作，在此基础上还增加了许多其他的操作，如赋值操作、聚集操作等
  - 数据库语言可以基于这三种抽象运算来设计
    - 用“键盘符号”来替换抽象的数学符号
    - 用易于理解的符号组合来表达抽象的数学符号
    - 例如：ISBL语言---基于关系代数的数据库语言
    - 再例如：Ingres系统的QUEL语言

## 6.总结

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210817161637971.png" alt="image-20210817161637971" style="zoom:50%;" />

