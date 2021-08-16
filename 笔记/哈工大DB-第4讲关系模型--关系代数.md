# 哈工大DB-第4讲关系模型--关系代数

[TOC]

[Latex数学符号表网址](https://blog.csdn.net/anscor/article/details/80878285)

## 0.本讲学什么

1. 关系代数之基本操作
2. 关系代数之扩展操作
3. 关系代数之组合与应用训练
4. 关系代数之复杂扩展操作(选学)

**重点与难点**

- 关系代数基本操作：并、差、积、选择、投影、(更名)。
- 关系代数扩展操作：交、$\theta$​-连接、自然连接。
- 关系代数复杂扩展操作：除、外连接
- 书写关系代数的基本思维训练：“一个集合，施加一个操作得到一个集合，依次施加关系代数操作，进而得到所需结果”“**以集合为中心**”


### 1.关系代数概述

### 1.1关系代数运算特点

- 基于集合，提供了一系列的关系代数操作：并、差、笛卡尔积(广义积)、选择、投影和更名等基本操作
- 以及交、 连接和关系除等扩展操作，是一种集合思维的操作语言。
- 关系代数操作以一个或多个关系为输入，结果是一个新的关系。
- 用对关系的运算来表达查询，需要指明所用操作, 具有一定的过程性。
  - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816161432958.png" alt="image-20210816161432958" style="zoom:50%;" />
- 是一种抽象的语言，是学习其他数据库语言，如SQL等的基础

### 1.2关系代数运算的基本操作

#### 1.2.1 集合操作--并、交、差、笛卡尔积

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816161612137.png" alt="image-20210816161612137" style="zoom: 67%;" />

#### 1.2.2 纯关系操作--投影、选择、连接、除

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816161701090.png" alt="image-20210816161701090" style="zoom: 67%;" />



## 2.关系代数的基本操作--并、差、积、选择、投影

### 2.1关系代数运算的约束--并相容性

<font color=blue>某些关系代数操作，如并、差、交等，需满足“并相容性”</font>

**并相容性**--衡量了两个关系是否是可比的(可以理解为两个关系的结构要相同，我们才能进行某些操作)

- 参与运算的两个关系及其相关属性之间有一定的对应性、**可比性**或意义关联性
- 定义：关系R与关系S存在相容性，当且仅当：
  - (1) 关系R和关系S的**属性数目必须相同**；
  - (2) 对于任意i，关系R的第i个属性的域必须和关系S的第i个属性的**域相同**
    - 假设：R(A1, A2, … , An) , S(B1, B2, … ,Bm)R和S满足并相容性：
      - n = m 并且 Domain(Ai) = Domain(Bi)
- **并相容性只需要属性数目相同，并且两个关系能找到一种一一对应，使得对应的两个属性的域相同即可**
  - **而不需要关系名字相同**

**并相容性的示例**

- STUDENT(SID char(10), Sname char(8), Age char(3)) 
- PROFESSOR(PID char(10), Pname char(8), Age char(3)) 
- 关系STUDENT与关系PROFESSOR是相容的，因为：
  - (1) 关系R和关系S的属性数目都是3
  - (2) 关系R的属性SID与关系S的属性PID的域都是char(10)
  - (3) 关系R的属性Sname与关系S的属性Sname的域都是char(8)
  - (4) 关系R的属性Age与关系S的属性Age的域都是char(3)

### 2.2“并”操作--将两个并相容的关系合并为一个

**并(Union)**--**两个关系的元组合并，并去掉重复的元组**

- 定义：假设关系R和关系S**是并相容的**，则关系R与关系S的并运算结果也是一个关系，记作：R ∪S
- 它由或者**出现在关系R中，或者出现在S中的元组**构成。
- 数学描述： $R∪S ={ t | t \in R \or t \in S }$ ，其中t是元组
- **并运算是将两个关系的元组合并成一个关系，在合并时去掉重复的元组。**
- **R ∪S 与 S ∪R 运算的结果是同一个关系**
- **汉语中**的**“或者…或者…”**通常意义是**并运算**的要求。
- 首先要准确理解汉语的查询要求，然后再找到正确的操作

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816162849606.png" alt="image-20210816162849606" style="zoom:50%;" />



### 2.3“差”操作--也需并相容为前提

**差(Difference)**---**以某关系为基，在此关系中去掉另一关系的元组**

- 定义：假设关系R 和关系S**是并相容的**，则关系R 与关系S 的差运算结果也是一个关系，记作：$R-S$
- 它由**出现在关系R中但不出现在关系S中的元**组构成。
- 数学描述： $R - S = \{ t | t\in R \and t\notin S\}$​ ，其中t是元组
- $R-S$​与 $S-R$​​ 是不同的
- **汉语中**的**“是…但不含…”**通常意义是**差运算**的要求。

示例:

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816163323944.png" alt="image-20210816163323944" style="zoom:50%;" />

### 2.4“笛卡尔积”操作--两个关系的元组进行所有可能的拼接组合

**广义笛卡尔积 (Cartesian Product)**---**两个关系的元组进行所有可能的拼接操作，生成新的一个元组集合，将多个表组合以便操作**

- 定义：关系R (<a1 , a2, …, an >) 与关系S(<b1, b2, …, bm >) 的广义笛卡尔积(简称广义积,或 积 或笛卡尔积) 运算结果也是一个关系，记作： R x S
-  它由关系R中的元组与关系S的元组进行**所有可能的拼接(或串接)**构成。
- 数学描述： $R\times S =\{ <a_1, …, a_n, b_1, …, b_m> | <a_1, …,a_n> \in R\  \and <b1, …, bm> \in S\}$​
- 当一个**检索涉及到多个表时**(如学生表和课程表)，便**需要将这些表串接或拼接起来**，然后才能检索，这时，就要**使用广义笛卡尔积运算**。是后面学习各种连接运算的基础
- **R x S = S x R** ： R x S为R中的每一个元组都和S中的所有元组进行串接。 S x R为S中的每一个元组都和R中的所有元组进行串接。结果是相同的。
- 两个关系R和S，它们的属性个数分别为n和m(R是n度关系，S是m度关系)，则**笛卡尔积 R x S的属性个数 =n + m**。
  - 即元组的前n个分量是R中元组的分量，后m个分量是S中元组的分量(R x S是n+m度关系).
- 两个关系R和S，它们的元组个数分别为x和y(关系R的基数x, S的基数y), 则**笛卡尔积R x S的元组个数 = $x\times y$​**。
  - (R x S的基数是$x\times y$​). 

示例：

- 关系R的元组数目是3，度数是3; 
- 关系S的元组数目是4, 度数是3; 
- 则R x S的元组数目是12, 度数是6

### 2.5“选择”操作--从给定的关系中选择出满足条件的行组成新的关系

- 定义：给定一个关系R, 同时给定一个选择的条件condition(简记con), 选择运算结果也是一个关系，记作$\sigma_{condition}(R)$ 
- 由关系R中选择出满足给定条件condition的元组构成。
- 数学描述： $\sigma_{condition}(R)=\{t\in R \and con(t) ='真'\}$​​​​​ 
- condition的书写规则：
  - 指代所有潜在元组的**某个分量**时：设R(A1 ,A2 , … ,An), t是R的元组, **t 的分量记为t[Ai], 或简写为Ai**
  - 条件con由**逻辑运算符**+**比较表达式**组成
  - **逻辑运算符**：$\and, \or, \lnot $​​或写为 and , or, not
  - **比较表达式**：$X \theta Y$​, 其中X, Y 是t的分量、常量或简单函数, **$\theta$​是比较运算符,$\theta\in \{>, <,=,\neq\}$​​**
  - 优先级：条件的书写很重要，尤其是当不同运算符在一起时，要注意运算符的优先
    次序，优先次序自高至低为$括弧, \theta, \lnot,\and ,\or $​

示例：注意字符串的话记得写上 双引号“”

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816170303849.png" alt="image-20210816170303849" style="zoom:50%;" />

### 2.6“投影”操作--从给定关系中选出某些列组成新的关系

<font color=blue>投影是从给定关系中选择某些列组成新的关系。选择是从给定关系中选择满足条件的行组成新的关系</font>

**投影(Project)**

- 定义：给定一个关系R, 投影运算结果也是一个关系，记作 $\prod_A(R)$. 
- 从关系R中选出属性包含在A中的列构成。我们使用A来表明我们要选择哪些列。
- 数学描述： $\prod_{A_{i1},...,A_{ik}}(R)=\{<t[A_{i1}],...,t[A_{ik}]>|t\in R\}$
- 设R(A1 ,A2 , … ,An)
  - $\{ Ai1, Ai2, … ,Aik \}\subseteq \{ A1 ,A2 , … ,An \}$​
  - t[Ai]表示元组t中相应于属性Ai的分量
  - 投影运算可以对原关系的列在投影后重新排列，虽然列其实与位置无关。
- **投影之后如果产生重复的元组，应该删除。**
- 用户可以根据需要**通过投影、选择操作查询他所关心的数据信息**。

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816171346226.png" alt="image-20210816171346226" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816171417129.png" alt="image-20210816171417129" style="zoom:50%;" />

### 2.7小结

- 构造所需要的表：并、差、积
- 查询关心的数据：
  - 选择：保留某些行
  - 投影：保留某些列

### 2.8“更名”操作

$\rho_{新名字}(旧名字)$

上述操作把表的名字更改为新的名字。

## 3.关系代数的扩展操作

### 3.1“交”操作

**交(Intersection)**

- 定义：假设关系R和关系S是**并相容**的，则关系R与关系S的交运算结果也是一个关系，记作：R ∩S
- 由**同时出现在关系R和关系S中的元组构成**。
- 数学描述： $R\cap S =\{ t | t\in R \and t\in S \}$ ，其中t是元组
- R∩S 和 S∩R 运算的结果是同一个关系
- 交运算可以通过差运算来实现： $R\cap S =R-(R-S)=S-(S-R)$​​ 
- 汉语中的“**既…又…”，“…, 并且…”**通常意义是**交运算**的要求

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816180030012.png" alt="image-20210816180030012" style="zoom:50%;" />

### 3.2“$\theta $​​连接”操作--两个表进行笛卡尔积并选择某些行留下，而选择的标准则为这些行的列满足某些比较运算

$\theta$​-连接($\theta$​-Join, theta-Join)--使用这个操作就可以不需要先构造一个新的表，再进行选择和投影操作。这个操作可以理解为**笛卡尔积、投影、选择操作的组合**。

- 投影与选择操作只是对单个关系(表)进行操作, 而实际应用中往往涉及**多个表之间的操作**, 这就需要$\theta$-连接操作
- 比如：查询数据结构成绩在90分以上的学生姓名(涉及Student, Course, SC)
- 定义：给定关系R和关系S, R与S的$\theta$​​连接运算结果也是一个关系，记作$R \mathop{\bowtie}\limits_{A\theta B}S$​​ ，它由关系R和关系S的笛卡尔积中, 选取R中属性A与S中属性B之间满足$\theta$​条件的元组构成。
- 数学描述：$R \mathop{\bowtie}\limits_{A\theta B}S = \sigma_{t[A]\theta S[B]}(R\times S)$ 
  - 设$R(A1 ,A2 , … ,An), A\in\{ A1 ,A2 , … ,An\}\ \ S(B1 ,B2 , … ,Bm), B\in\{ B1 ,B2 , … ,Bm \}$​
  - t是关系R中的元组，s是关系S中的元组
  - **属性A和属性B具有可比性**
  - $\theta$是比较运算符, $\theta\in \{>, <,=,\neq\}$​
  - 在实际应用中，$\theta$​​-连接操作经常与投影、选择操作一起使用
- **操作步骤：**
  - 两个关系笛卡尔积
  - 然后对积后的关系进行选择，选择的条件就是$A\theta B$​
  - **当引入连接操作后，DBMS可直接进行连接操作，而不必先形成笛卡尔积**

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816183126849.png" alt="image-20210816183126849" style="zoom:50%;" />

#### $\theta$连接与自身连接

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816183921924.png" alt="image-20210816183921924" style="zoom:50%;" />



### 3.3“等值-连接”操作--$\theta$连接的特例

**等值连接(Equi-Join)**

- 定义：给定关系R和关系S, R与S的等值连接运算结果也是一个关系，记作$R \mathop{\bowtie}\limits_{A=B}S$​​​ 
- 由关系R和关系S的笛卡尔积中选取选取**R中属性A与S中属性B上值相等的元组**所构成。
- 数学描述：$R \mathop{\bowtie}\limits_{A=B}S = \sigma_{t[A]=S[B]}(R\times S)$​​ 
- **当$\theta$-连接中运算符为“＝”时，就是等值连接，等值连接是$\theta$​-连接的一个特例；**
- 广义积的元组组合并不是都有意义的，另广义积的元组组合数目也非常庞大，因此**采用$\theta$-连接/等值连接运算可大幅度降低中间结果的保存量，提高速度**。

示例:

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816184547082.png" alt="image-20210816184547082" style="zoom:50%;" />

注意，最后连接的结果还是会有列honor_type和type，因此需要投影操作。

### 3.4 “自然连接”操作--特殊的等值连接，使用最普遍的

**自然连接(Natural-Join)**--两个关系中，**有属性名的相同的列**，这些列组中，**找到所有的属性值相等的行(准备拼接的双方的候选行，所有的同名属性的值一定得一模一样，见示例)，这些行进行笛卡尔积拼接**，**并删除相同属性名的列**

- 定义：给定关系R和关系S, R与S的自然连接运算结果也是一个关系，记作 $R \mathop{\bowtie}S$​ 
- 由关系R和关系S的笛卡尔积中**选取相同属性组B上值相等**的元组所构成。
- 数学描述：$R \mathop{\bowtie}S = \sigma_{t[A]=S[B]}(R\times S)$ 
- **自然连接是一种特殊的等值连接**
- 要求**关系R和关系S必须有相同的属性组B**(如R,S共有一个属性B1,则B是B1 , 如R, S共有一组属性B1, B2, …, Bn，则B是这些共有的所有属性)
- **R, S属性相同，值必须相等才能连接**，即R.B1 = S.B1 and R.B2 = S.B2 … and R.Bn = S.Bn才能连接
- 要在结果中**去掉重复的属性列**(因结果中R.Bi 始终是等于S.Bi 所以可只保留一列即可)

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816185519879.png" alt="image-20210816185519879" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816185540350.png" alt="image-20210816185540350" style="zoom:50%;" />

### 3.5小结

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816185756290.png" alt="image-20210816185756290" style="zoom:50%;" />

- 选出哪些表需要用
- 然后考虑怎么使用操作，可否用连接操作替代
- 选择运算选出需要的行
- 投影运算选出要的列

- 由里向外进行书写。
- **检查操作是否满足操作的相容性前提条件。**
- 严格检查结果是否正确。

### 3.6书写关系代数的思维

思维训练PPT195--202

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816192406142.png" alt="image-20210816192406142" style="zoom:50%;" />

## 4.关系代数的复杂扩展操作

### 4.1“除”操作--常用于求解“查询… 全部的/所有的…”问题

- 应用场景：除法运算经常用于**求解“查询… 全部的/所有的…”问题**
- <font color=blue>前提条件：</font>前提条件：给定关系R(A1 ,A2 , … ,An)为n度关系，关系S(B1 ,B2 , … ,Bm)为m度关系 。如果可以进行关系R与关系S的除运算，**当且仅当：属性集{ B1 ,B2 , … , Bm }是属性集{ A1 ,A2 , … ,An }的真子集，即m < n。**
- 定义：**关系R 和关系S的除运算结果也是一个关系，记作$R\div S$​**，分两部分来定义:

  - 1.先定义$R\div S$​​**结果的属性**应有哪些？
    - **从R中去掉所有S的属性**
    - 设属性集{C1,C2, … ,Ck } = {A1,A2, … ,An } – {B1,B2, … ,Bm }, 则有k=n–m
    - 则$R\div S$​​结果关系是：**k度(n-m度)关系，由{C1,C2, … ,Ck }属性构成**
  - 2.再定义$R\div S$​​的**元组怎样形成**？
    - **结果元组与S中的每一个元组组合形成的都必须是R中的元组。**
    - 再设关系R (<a1, …, an>)和关系S (<b1, …, bm >)
    - 那么$R\div S$结果关系为元组 <c1, …, ck>的集合，**元组 <c1, …, ck>**满足下述条件：
      - 它**与S中<font color=blue>每一个</font>元组<b1, …, bm >组合形成的一个新元组**都**是R中的某一个元组<a1, …, an>** 。(其中，a1, …, an ,b1, …, bm, c1, …, ck分别是属性A1 , … ,An,B1 , … ,Bm C1 , … ,Ck 的值)
- 数学描述： $R\div S = \{t|t \in \prod_{R-S}(R) \and \forall u \in S (tu \in R) \}=\prod_{R-S}(R)-\prod_{R-S}((\prod_{R-S}(R)\times S)-R)$​
    - $tu$​是组合起来形成新元组的意思
    - 第二个等号的解释：在R砍掉S的属性列后剩余的属性列中，找出那些不能和S拼接成R的属性组合
    - <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816213606668.png" alt="image-20210816213606668" style="zoom:50%;" />

示例：

- 求值：
- 先求出剩余的属性
- 再去R里面找有S里面有的那些行作为候选
- 如果S里面有多行，则结果元组与这些行拼接都必须在R里面存在
- 如果S里面有多列，其实和一列是没有区别的

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816213030144.png" alt="image-20210816213030144" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816213839859.png" alt="image-20210816213839859" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816213905987.png" alt="image-20210816213905987" style="zoom:50%;" />

### 4.2“外连接”操作--自然连接中失配的元组和空值配对存放在结果中就为外连接

**外连接(Outer Join)**

- 定义：两个关系R与S进行连接时，如果关系R(或S)中的元组在S(或R)中**找不到相匹配的元组**， **为了避免该元组信息丢失**，从而**将该元组与S(或R)中假定存在的全为空值的元组形成连接**(人话就是：找不到人配对就和空值配对)，放置在结果关系中，这种连接称之为外连接(Outer Join)。
- 如果没有匹配的元组，也能形成新的元组，没匹配上的元组的原值填充到新元组中，而缺失的值则用空值"?"代替
- <img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816214852324.png" alt="image-20210816214852324" style="zoom:50%;" />

#### 多种外连接

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816214929000.png" alt="image-20210816214929000" style="zoom:67%;" />

示例：

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816215146956.png" alt="image-20210816215146956" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816215203402.png" alt="image-20210816215203402" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816215224199.png" alt="image-20210816215224199" style="zoom:50%;" />

## 5.第四讲总结

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816215508846.png" alt="image-20210816215508846" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816215913812.png" alt="image-20210816215913812" style="zoom:50%;" />

<img src="E:\AAAAAAAuniPPT\A假期学习\A暑假新增\Class_Database(git)\CSclass-DB\笔记\${图片}\image-20210816215930701.png" alt="image-20210816215930701" style="zoom:50%;" />
