<!-- TOC -->

 * [RDBMS(Relational Database Manager System)](#rdbmsrelational-database-manager-system)
      * [什么是RDBMS?](#什么是rdbms)
         * [什么是关系型数据库?](#什么是关系型数据库)
            * [关系型数据库(SQL)与非关系型数据库(NoSQL)的区别](#关系型数据库sql与非关系型数据库nosql的区别)
         * [RDBMS常见知识点](#rdbms常见知识点)
            * [键是什么?](#键是什么)
            * [超键 / 候选键 / 主键 / 外键？](#超键--候选键--主键--外键)
            * [联合主键和复合主键](#联合主键和复合主键)
            * [DDL,DML,DCL,DQL,TCL](#ddldmldcldqltcl)
            * [DROP , TRUNCATE , DELETE区别](#drop--truncate--delete区别)
            * [数据库设计范式(Normal Form)?](#数据库设计范式normal-form)
            * [视图是什么?](#视图是什么)
            * [视图与表有什么不同?](#视图与表有什么不同)
            * [视图的优点](#视图的优点)
            * [视图的缺点](#视图的缺点)
            * [存储过程是什么?](#存储过程是什么)
            * [存储过程的优点](#存储过程的优点)
            * [存储过程的缺点](#存储过程的缺点)
            * [触发器是什么?](#触发器是什么)
            * [临时表](#临时表)
            * [连接](#连接)
         * [索引](#索引)
            * [什么是索引?](#什么是索引)
            * [索引的优点](#索引的优点)
            * [索引的缺点](#索引的缺点)
            * [B树和B 树区别](#b树和b树区别)
            * [Hash索引](#hash索引)
         * [索引类型](#索引类型)
            * [主键索引(Primary Key)](#主键索引primary-key)
            * [二级索引(辅助索引)](#二级索引辅助索引)
         * [聚集索引与非聚集索引](#聚集索引与非聚集索引)
            * [聚集索引](#聚集索引)
            * [聚集索引的优点](#聚集索引的优点)
            * [聚集索引的缺点](#聚集索引的缺点)
            * [非聚集索引](#非聚集索引)
            * [非聚集索引的优点](#非聚集索引的优点)
            * [非聚集索引的缺点](#非聚集索引的缺点)
            * [非聚集索引一定回表查询吗(覆盖索引)?](#非聚集索引一定回表查询吗覆盖索引)
            * [覆盖索引](#覆盖索引)
         * [索引创建原则](#索引创建原则)
            * [单列索引](#单列索引)
            * [联合索引(多列索引)](#联合索引多列索引)
            * [最左前缀原则](#最左前缀原则)
         * [索引创建注意点](#索引创建注意点)
            * [最左前缀原则](#最左前缀原则-1)
            * [选择合适的字段](#选择合适的字段)
            * [不合适的字段](#不合适的字段)
            * [尽可能的考虑建立联合索引而不是单列索引](#尽可能的考虑建立联合索引而不是单列索引)
            * [考虑在字符串类型的字段上使用前缀索引代替普通索引](#考虑在字符串类型的字段上使用前缀索引代替普通索引)
            * [使用索引一定能提高查询性能吗?](#使用索引一定能提高查询性能吗)
      * [Mysql](#mysql)
         * [Mysql是什么?](#mysql是什么)
            * [Mysql架构](#mysql架构)
         * [Mysql存储引擎](#mysql存储引擎)
            * [InnoDB](#innodb)
            * [MyISAM](#myisam)
            * [MRG_MyISAM](#mrg_myisam)
            * [MEMORY](#memory)
            * [BLACKHOLE](#blackhole)
            * [CSV](#csv)
            * [ARCHIVE](#archive)
            * [FEDERATED](#federated)
            * [PERFORMANCE_SCHEMA](#performance_schema)
         * [事务](#事务)
            * [什么是事务?](#什么是事务)
            * [事务的四大特性(ACID)](#事务的四大特性acid)
            * [DBMS中实现事务持久性的子系统是什么](#DBMS中实现事务持久性的子系统是什么)
            * [事务的隔离级别](#事务的隔离级别)
            * [事务隔离级别引发的问题](#事务隔离级别引发的问题)
            * [快照读](#快照读)
         * [数据库锁](#数据库锁)
            * [数据库锁机制是什么](#数据库锁机制是什么)
            * [乐观锁和悲观锁](#乐观锁和悲观锁)
            * [共享锁和独占锁(排他锁)](#共享锁和独占锁排他锁)
            * [行锁，表锁，页锁](#行锁表锁页锁)
            * [行锁基于索引](#行锁基于索引)
         * [Mysql Log日志](#mysql-log日志)
            * [binlog](#binlog)
            * [redolog](#redolog)
            * [undolog](#undolog)
         * [Mysql优化](#mysql优化)
            * [Explain执行计划](#explain执行计划)
            * [开启慢查询日志](#开启慢查询日志)
            * [为什么要求字段尽量设置为NOT NULL?](#为什么要求字段尽量设置为not-null)
            * [为什么主键尽量设置成有序和整型?](#为什么主键尽量设置成有序和整型)
         * [Mysql数据类型](#mysql数据类型)
            * [UTF8和UTF8MB4](#utf8和utf8mb4)
            * [CHAR 和 VARCHAR](#char-和-varchar)
            * [TIMESTAMP 和 DATETIME](#timestamp-和-datetime)
            * [如何在TIMESTAMP和DATETIME之中选择?](#如何在timestamp和datetime之中选择)
         * [SQL Practice](#sql-practice)
            * [1](#1)
            * [2](#2)

<!-- /TOC -->


# RDBMS(Relational Database Manager System)

````text
如有错误之处，敬请指教。
````

PS:部分图片源于网络,如有侵权，请联系俺，俺会立刻删除。


## 什么是RDBMS?
关系型数据库管理系统。
关系型数据库管理系统是管理关系型数据库的软件系统。


### 什么是关系型数据库?
**关系型数据库是指采用了关系模型来组织数据的数据库。
关系型数据库以行和列的形式来存储数据，以便于用户理解。**
关系型数据库一系列的行和列的集合被称为数据表，而数据库则由一组数据表构成。


#### 关系型数据库(SQL)与非关系型数据库(NoSQL)的区别
关系型数据库与非关系型数据库主要有以下区别:

- 存储结构
>关系型数据库按照结构化的方式存储数据，需要先定义好数据库表的字段，再存储数据。
>这样做的好处就是可靠性比较高，但是如果后期应用需要功能，需要扩展表的话，会有些受限。
>
>非关系型数据库存储的结构则不像关系型数据库那样固定，相对来说较为灵活，
>可以根据数据内容调整数据库的结构。

- 存储方式
>关系型数据库大多都使用行和列这样的表格关系存储数据。
>
>非关系型数据库存储数据的方式是不固定的，有的采用K-V及键值对存储，
>有的采用文档存储，还有的图数据库使用图结构存储。

- SQL标准
>关系型数据库采用结构化的语言SQL来对数据库进行操作，并且SQL已成为大多数关系型数据库的标准规范。
> 
>非关系型数据库则各自为战，一直没有一个统一的标准，每种厂商提供的数据库规范都不一样。

- 读写性能
>关系型数据库强调数据的一致性，所以在遇到高并发读写操作时，会显得力不从心。
>
>非关系型数据库强调BASE理论:
>**Basically Available(基本可用), Soft-state(软状态), Eventual Consistency(最终一致性)，**
>它允许一定程度的数据不一致，但保证数据的最终一致性。
>因此，面对高并发读写操作时，表现的会比关系型数据库好的多，
>这也是redis,memcache这类高性能的NoSQL数据库被用于缓存的主要原因。

---

### RDBMS常见知识点

#### 键是什么?
键是描述数据表中某些特殊的属性列。

```text
假设有一个学生表和一个班级表:
学生表有: 学号，身份证号，性别等属性
班级表有: 班级id，班级名等属性.
```

#### 超键 / 候选键 / 主键 / 外键？
* 超键: 超键是能唯一标识数据表中的记录的**属性集的集合**。
>超键可以是一个属性，也可以是属性组合。
>如学生表中的学号可以作为学生的唯一标识，
>身份证号也可以作为学生的唯一标识,那么与这2个属性任意搭配的集合，
>都可以作为学生表的超键:
>[[学号]，[身份证号],[学号,身份证号]，[学号，性别]，[身份证号，性别]...]等等。

* 候选键: 候选键是能唯一标识数据表中的记录的**属性的集合。**
>可以把候选键看作是最小粒度的超键，即没有冗余的超键。
>学生表中的候选键为:[[学号]，[身份证号]]。
>但是不能有[学号，身份证号]，因为学号和身份证号同时存在就不是最小粒度了。

* 主键: **主键是能唯一标识数据表中的记录的属性列。**
>看起来主键和候选键区别不大。
>但是候选键可以是一个集合,同时包括[学号],[身份证号]，
>而主键是从候选键里选出一个属性出来，要么是[学号]，要么是[身份证号]。(不考虑联合主键哈)

* 外键: **外键是约束一个数据表和另一个数据表表的关系的属性列。**
>如何确定学生在哪个班级呢?或者说如何确定某个班级有哪些学生呢?
>一个班级可以有多个学生.这就属于一对多关系。
>可以在学生表中加一个班级id的外键列，与班级表的班级id关联，
>这样就可以确定学生与班级的关系了。

#### 联合主键和复合主键

```text
网上有文章说联合主键和复合主键有区别，但我个人认为没区别。
```

**在我看来联合主键和复合主键都是以多个属性列共同组合的主键，
它们以组合的形式保证数据的唯一性。**

>有的同学说联合主键是多个主键组合成的主键，
>而我想反驳:一个表只有一个主键呀，哪来的那么多主键。
>我估摸着有同学大概是想说多个唯一属性的列组成的主键吧，那还不是属于组合主键。。
>当然，也可能是我功力不足，认识不到吧。

#### DDL,DML,DCL,DQL,TCL
* DDL(Data Define Language:数据定义语言):**DDL的功能是用于定义数据库中的模式(Schema)，
模式包含了表，视图，存储过程等内容。** 这里准确来说应该是定义数据库的三级模式:外模式，模式(逻辑模式，概念模式)和内模式。

>DDL的关键字有: CREATE , ALTER , DROP等。

- DML(Data Manipulation Language:数据操纵语言):**DML的功能是用于操作数据库中的数据。** 

>DML的关键字有: SELECT , DELETE , UPDATE , INSERT等。

- DCL(Data Control Language:数据控制语言): **DCL的功能是用于设置数据库的用户权限。** 

>DCL的关键字有: GRANT,REVOKE等。

- TCL(Transaction Control Language:事务控制语言): **TCL的功能是用于管理事务。** 

>TCL的关键字有: BEGIN , COMMIT , ROLLBACK等。

- DQL(Data Query Language:数据查询语言): 数据查询语言，它属于DML。

>DQL的主要关键字就是SELECT了。

#### DROP , TRUNCATE , DELETE区别

- DROP: 删除表(包括表的所有索引和数据)或数据库。**DROP属于DDL，操作不可回滚。**

- TRUNCATE: 删除表中的所有数据，如果有字段是自增的，那么该字段将重新从0开始。
**TRUNCATE属于DDL，操作不可回滚。**

- DELETE: 删除表中指定的数据，如果没有指定条件，将删除所有数据。**DELETE属于DML，操作可回滚。**


#### 数据库设计范式(Normal Form)?

* 第一范式: **所有字段都是不可分解的原子属性。**
>假设在一张用户表中有一个字段为地址。
>但地址其实就不是一个原子属性，
>因为地址可以分成: 国家 + 省份 + 城市 + 区域 + 街道等属性，
>所以需要以最小粒度为单位设置表的属性。比如年龄，它仅仅代表年龄，并不能再分割。

* 第二范式: **第二范式在第一范式的基础上，所有属性必须依赖于主键，不能依赖部分主键。**
>一个表必须所有的非主键属性都必须依赖于主键，而且不能只依赖部分主键，
>假设有一张学生教师表，字段为:
>学号，学生姓名 ，教师编号，教师姓名。

| 学号(PK)|学生姓名 | 教师编号(PK) | 教师姓名　|  
| :----:| :----: | :----: |  :----: |
| 1 |　guang19 |     1    |  qsjz  |   

>其中学号与教师编号为联合主键，学生姓名依赖于学号，而并不依赖于教师编号，
>所以学生表不符合第二范式。
>
>正确的做法是将学生教师表拆分为2张表:学生表和教师表，
>并添加一张中间表来建立学生与老师的关系(一对一或一对多)。
>
>学生表的字段为:学号，学生姓名。
>教师表的字段为:教师编号，教师姓名。

学生表:

| 学号(PK)|学生姓名 | 
| :----:| :----: | 
| 1 |　guang19 |  
 
教师表:

| 教师编号(PK)|教师姓名 |
| :----:| :----: |
| 1 |　qsjz |  

中间表:

| 学号(PK) | 教师编号 |
| :----:| :---: |
| 1   |   1  |

* 第三范式: **第三范式在第二范式的基础上，属性不能间接依赖于主键，必须直接依赖于主键。**
>假设有一张学生表的字段为:
>学号，学生姓名，班级编号，班级名称。

| 学号(PK)|学生姓名 | 班级编号 | 班级名称　|  
| :----:| :----: | :----:| :----: |
| 1 |　guang19 | 1 | qsjz5|   

>其中学号为主键，但是班级名称依赖于班级编号，班级编号再依赖于学号。
>这样班级名称与学号之间并不是直接性依赖，而是传递性依赖。
>
>可以将学生表拆分为:学生表和班级表，其中:
>学生表的字段为: 学号，学生姓名，班级编号。
>班级表的字段为:班级编号 ， 班级名称。

学生表:

| 学号(PK)|学生姓名 | 班级编号 |
| :----:| :----:| :----: |
| 1 |　guang19 | 1 |

班级表:

| 班级编号(PK)|班级名称 |
| :----:| :----: |
| 1 |　qsjz5 |


>**学生表的班级编号与班级表的班级编号就属于一种外键关系了，**
>2张表中也不再有传递依赖性的依赖关系了。


#### 视图是什么?
**视图是一种展示数据表特定结果的虚拟表。**
它主要用来做查询结果集的展示。


#### 视图与表有什么不同?
**数据表是存在物理文件中的，而于视图是虚拟存在的内存表。**
它实际上是一条编译好的Select SQL语句，没有任何数据。
**对视图的增删改查等操作实际上是对视图的基表的操作。**


#### 视图的优点
>视图的优点主要在于可以定制用户数据，让用户关注于其自定义数据本身，而不用理会无关的数据。


#### 视图的缺点
视图的主要缺点在于修改限制。
虽然视图主要是用来做结果集的查询展示的，
但是仍然可以对视图做出修改的操作(实际上是对基表做出修改)。
如果一个视图由多张基表的结果集组成，那么修改操作会变得很麻烦。

#### 存储过程是什么?
当用户使用DML SQL语句操作数据库时，数据库需要编译SQL后再执行。
**而存储过程则是用户为了完成特定的任务，
而预先在数据库中定义好并经过数据库编译后的一组SQL，**
用户通过指定存储过程的名字和参数来调用存储过程。

```text
存储过程类似于编程语言中的方法函数。 
```

#### 存储过程的优点
存储过程的优点主要在于它允许我们像编写函数一样定义SQL语句，非常的灵活。
并且存储过程是直接经过预编译直接存储在内存之中的，执行速度是很快的。

#### 存储过程的缺点
存储过程的缺点主要在于耗费数据库的资源，如果存储过程过多，那么占用的内存也是越多的。

>有的文章说存储过程的可移植性差，但应用程序的技术选型不应该是预先敲定的吗?

#### 触发器是什么?
触发器是在指定表上，当满足指定条件时会执行的SQL语句的集合。
**可以把触发器看做是特殊的存储过程，不过存储过程需要手动调用，
而触发器则是满足指定条件就会被触发。**

```text
触发器的触发事件有: UPDATE,DELETE,INSERT
触发时间有:Before,After
```

触发器缺点同存储过程一样。 

#### 临时表
临时表与普通数据表是相似的，不过临时表只在当前的连接之中有效，
当连接断开时，临时表就被销毁了。
因此，临时表可以保存一些临时的数据。

**使用SHOW TABLES命令是无法查看临时表的。**


#### 连接
连接分为:内连接，外连接和交叉连接。

* 内连接:内连接只返回连接表的匹配的数据。

* 外连接:外连接分为:左外连接，右外连接和全外连接。

  * 左外连接:左外连接会返回左表所有的行，即使右表中没有匹配的行。
  
  * 右外连接:右外连接返回右表所有的行，即使左表中没有匹配的行。
  
  * 全外连接:全外连接返回所有表的所有行，即使表的数据不匹配。

* 交叉连接:**交叉连接又称为笛卡尔积**，它不同于其他连接，交叉连接无需指定条件。
**它将一张表的每一行与另一张表的所有行全部匹配一遍，效率非常低，而且使用交叉连接的情况较少



---


### 索引

#### 什么是索引?
**索引是一种用于快速查询和检索数据的数据结构。
常见的索引结构有: B树， B+树和Hash。**

**索引的作用就相当于目录的作用。**

>打个比方: 我们在查字典的时候，如果没有目录，
>那我们就只能一页一页的去找我们需要查的那个字，速度很慢。
>
>如果有目录了，我们只需要先去目录里查找字所在的页数，然后直接翻到那一页就行了。

#### 索引的优点
**索引最大的优点就是数据的检索效率高，这也是创建和使用索引的原因。
毕竟大部分系统的读请求总是大于写请求的。**

#### 索引的缺点
* **创建索引和维护索引需要耗费许多时间** : 当对表中的数据进行增删改的时候，如果数据有索引，
那么索引也需要动态的修改，会降低SQL执行效率。

* **占用物理存储空间** : 索引需要使用物理文件存储，也会耗费一定空间。

#### B树和B+树区别

* **B树的所有节点既存放 键(key) 也存放 数据(data);**
而**B+树只有叶子节点存放 key 和 data，其他的内节点只存放key。**

* **B树的叶子节点都是独立的;B+树的叶子节点有一条引用链指向与它相邻的叶子节点。**

* **B树的检索的过程相当于对范围内的每个节点的关键字做二分查找，
可能还`没有到达叶子节点，检索就结束了。**
而B+树的检索效率就很稳定了，**任何查找都是从根节点到叶子节点的过程，
且叶子节点的顺序检索很明显。**

![B+树](../img/database/mysql/B+树.png)

#### Hash索引
* **Hash索引定位快**
>Hash索引指的就是Hash表，最大的优点就是能够在很短的时间内，
>根据Hash函数定位到数据所在的位置，这是B+树所不能比的。

* **Hash冲突**
>知道HashMap或HashTable的同学，相信都知道它们最大的缺点就是Hash冲突了。
>不过对于数据库来说这还不算最大的缺点。

* **Hash索引不支持顺序和范围查询(Hash索引不支持顺序和范围查询是它最大的缺点。)**
>试想一种情况:

````text
SELECT * FROM tb1 WHERE id < 500;
````

>B+树是有序的，在这种范围查询中，优势非常大，
>直接遍历比500小的叶子节点就够了。
>
>而Hash索引是根据hash算法来定位的，可能还要把 1 - 499的数据，
>每个都进行一次hash计算来定位，就算不这样做，也需要全表扫描吧。 


### 索引类型

#### 主键索引(Primary Key)
**数据表的主键列使用的就是主键索引。**

**一张数据表有只能有一个主键，并且主键不能为null，不能重复。**

**在mysql的InnoDB的表中，当没有显示的指定表的主键时，
InnoDB会自动先检查表中是否有唯一索引的字段。
如果有，则选择该字段为默认的主键，否则InnoDB将会自动创建一个6Byte的自增主键。**

#### 二级索引(辅助索引)
**二级索引又称为辅助索引，是因为二级索引的叶子节点存储着主键。
也就是说，通过二级索引，可以定位主键的位置。**

唯一索引，普通索引，前缀索引等索引属于二级索引。

PS:不懂的同学可以暂存疑，慢慢往下看，后面会有答案的，也可以自行搜索。

1. **唯一索引(Unique Key)**: 唯一索引也是一种约束。**唯一索引的属性列不能出现重复的数据，
但是允许数据为NULL，一张表允许创建多个唯一索引。**
建立唯一索引的目的通常都是为了该属性列的数据的唯一性，而不是为了查询效率。

2. **普通索引(Index)**:普通索引的唯一作用就是为了快速查询数据。
**一张表允许创建多个普通索引，并允许数据重复和NULL。**

3. **前缀索引(Prefix)**:**前缀索引只适用于字符串类型的数据。**
前缀索引是对文本的前几个字符创建索引，相比普通索引建立的数据更小因为只取前几个字符。

4. **全文索引(Full Text)**:全文索引主要是为了检索大文本数据中的关键字的信息，
是目前搜索引擎数据库使用的一种技术。
Mysql5.6之前只有MYISAM引擎支持全文索引，5.6之后InnoDB也支持了全文索引。

二级索引:
![B+树二级索引](../img/database/mysql/B+树二级索引.png)


### 聚集索引与非聚集索引

#### 聚集索引
**聚集索引即索引结构和数据一起存放的索引。**

**主键索引属于聚集索引。**

在Mysql中，InnoDB引擎的表的.ibd文件就包含了该表的索引和数据，
对于InnoDB引擎表来说，该表的索引(B+树)的每个非叶子节点存储索引，
叶子节点存储索引和索引对应的数据。

#### 聚集索引的优点

聚集索引的查询速度非常的快，因为整个B+树本身就是一颗多叉平衡树，
叶子节点也都是有序的，定位到索引的节点，就相当于定位到了数据。

#### 聚集索引的缺点
* 依赖于有序的数据
>因为B+树是多路平衡树，如果索引的数据不是有序的，
>那么就需要在插入时排序，如果数据是整型还好，
>否则类似于字符串或UUID这种又长又难比较的数据，插入或查找的速度肯定比较慢。

* 更新代价大
>如果对索引列的数据被修改时，那么对应的索引也将会被修改，
>而且况聚集索引的叶子节点还存放着数据，修改代价肯定是较大的，
>所以对于主键索引来说，主键一般都是不可被修改的。

#### 非聚集索引

**非聚集索引即索引结构和数据分开存放的索引。**

**二级索引属于非聚集索引。**

MYISAM引擎的表的.MYI文件包含了表的索引，
该表的索引(B+树)的每个叶子非叶子节点存储索引，
叶子节点存储索引和索引对应数据的指针，指向.MYD文件的数据。

**非聚集索引的叶子节点并不一定存放数据的指针，
因为二级索引的叶子节点就存放的是主键。**

#### 非聚集索引的优点
* 更新代价比聚集索引要小
>非聚集索引的更新代价就没有聚集索引那么大了，非聚集索引的叶子节点是不存放数据的

#### 非聚集索引的缺点
* 跟聚集索引一样，非聚集索引也依赖于有序的数据

* 可能会二次查询(回表)
>这应该是非聚集索引最大的缺点了。 
>当查到索引对应的指针或主键后，可能还需要根据指针或主键再到数据文件或表中查询。

这是Mysql的表的文件截图:

![Mysql表文件截图](../img/database/mysql/Mysql索引文件截图.png)

聚集索引和非聚集索引:

![B+树聚集索引](../img/database/mysql/B+树索引.png)

#### 非聚集索引一定回表查询吗(覆盖索引)?

**非聚集索引不一定回表查询。**

>试想一种情况，用户准备使用SQL查询用户名，而用户名字段正好建立了索引。

````text
 SELECT name FROM table WHERE name='guang19';
````

>那么这个索引的key本身就是name，查到对应的name直接返回就行了，无需回表查询。

**即使是MYISAM也是这样，虽然MYISAM的主键索引确实需要回表，因为它的主键索引的叶子节点存放的是指针。
但是如果SQL查的就是主键呢?**

```text
SELECT id FROM table WHERE id=1;
```

>主键索引本身的key就是主键，查到返回就行了。
>这种情况就称之为覆盖索引了。

#### 覆盖索引
**覆盖索引即需要查询的字段正好是索引的字段，那么查找到该索引的字段就可以返回了，而无需回表查询。**

>如主键索引，如果一条SQL需要查询主键，那么正好根据主键索引就可以查到主键。
>
>再如普通索引，如果一条SQL需要查询name，name字段正好有索引，
>那么直接根据这个索引就可以查到数据，也无需回表。

覆盖索引:
![B+树覆盖索引](../img/database/mysql/B+树覆盖索引.png)


### 索引创建原则

#### 单列索引
单列索引即由一列属性组成的索引。

#### 联合索引(多列索引)
联合索引即由多列属性组成索引。

#### 最左前缀原则
>假设创建的联合索引由三个字段组成: 

```text
ALTER TABLE table ADD INDEX index_name (num,name,age)
```

>那么当查询的条件为:
>num 或 (num AND name) 或 (num AND name AND age)时，索引才生效。
>所以在创建联合索引时，尽量把查询最频繁的那个字段作为索引的最左(第一个)字段。
>查询的时候也尽量以这个字段为第一条件。

**但可能由于版本原因(我的mysql版本为8.0.x),我创建的联合索引，
相当于在联合索引的每个字段上都创建了相同的索引:**

![联合索引(多列索引)](../img/database/mysql/联合索引.png)

无论是否符合最左前缀原则，每个字段的索引都生效:

![联合索引生效](../img/database/mysql/联合索引之查询条件生效.png)

### 索引创建注意点

#### 最左前缀原则
>虽然我目前的Mysql版本较高，好像不遵守最左前缀原则，索引也会生效。
>但是我们仍应遵守最左前缀原则，以免版本更迭带来的麻烦。

#### 选择合适的字段

* 不为NULL的字段: 索引字段的数据应该尽量不为NULL，因为对于数据为NULL的字段，数据库较难优化。
如果字段频繁被查询，但又避免不了为NULL，建议使用0,1,true,false
这样语义较为清晰的短值或短字符作为替代。

* 被频繁查询的字段: 我们创建索引的字段应该是查询操作非常频繁的字段。

* 被作为条件查询的字段: 被作为WHERE条件查询的字段，应该被考虑建立索引。

* 被经常频繁用于连接的字段: 经常用于连接的字段可能是一些外键列，外键列并不是一定要建立外键，
只是说该列涉及到表与表的关系。对于频繁被连接查询的字段，可以考虑建立索引，提高多表连接查询的效率。

#### 不合适的字段
* 被频繁更新的字段应该慎重建立索引: 虽然索引能带来查询上的效率，但是维护索引的成本也是不小的。
如果一个字段不被经常查询，反而被经常修改，那么就更不应该在这种字段上建立索引了。

* 不被经常查询的字段没有必要建立索引

#### 尽可能的考虑建立联合索引而不是单列索引

因为索引是需要占用磁盘空间的，可以**简单理解为每个索引都对应着一颗B+树。**
如果一个表的字段过多，索引过多，那么当这个表的数据达到一个体量后，
索引占用的空间也是很多的，且修改索引时，耗费的时间也是较多的。

如果是联合索引，多个字段在一个索引上，那么将会节约很大磁盘空间，
且修改数据的操作效率也会提升。

#### 考虑在字符串类型的字段上使用前缀索引代替普通索引
**前缀索引仅限于字符串类型，较普通索引会占用更小的空间，**
所以可以考虑使用前缀索引带替普通索引。

#### 使用索引一定能提高查询性能吗?
大多数情况下，索引查询都是比全表扫描要快的。
但是如果数据库的数据量不大，那么使用索引也不一定能够带来很大提升。



---



## Mysql

### Mysql是什么?
>Mysql是一个关系型数据库管理系统，由瑞典Mysql公司开发，现属于Oracle旗下产品。
>Mysql是最流行的关系型数据库之一，与它同类型的数据库还有SQL Server，Oracle，DB2等。

[Mysql官方文档](https://dev.mysql.com/doc/)

#### Mysql架构

Mysql总体架构可分为三层:应用层,服务层，存储引擎层:

![Mysql架构](../img/database/mysql/Mysql架构图.png)

- 应用层: 应用层是Mysql体系最上面的一层，接受客户端的连接请求。
应用层包含:连接处理，用户认证，安全管理等内容。
 
  - 连接处理: 当客户端向Mysql服务端发送一个请求后，Mysql 服务会从线程池中分配一个线程来对客户端连接进行处理。 
  
  - 用户认证: 当客户端请求连接后，服务端会根据用户名，密码等信息判断用户身份。
  
  - 安全管理(权限): 当客户端连接到Mysql服务端后，Mysql服务会验证用户的权限，以便限制用户的操作。

- 服务层: 服务层用于处理客户端的操作，是Mysql的核心模块，主要包括:SQL解析器，优化器和缓存等。

  - SQL解析器: sql解析器用于解析SQL语句，如果SQL有错误，则会提示相应的错误信息，如果没有错，则执行SQL优化。
    如果SQL是查询语句，那么首先会去缓存里查询，如果查询成功，就直接返回结果，
    不进行接下来的SQL优化。
  
  - 优化器: 优化器用于优化SQL语句，使得SQL的执行更加高效率。
  
  - 缓存: 缓存SQL查询的结果，提高SQL查询的效率。

- 存储引擎层: 存储引擎是Mysql数据持久化的核心。
Mysql是数据库肯定要存储数据，存储数据就要与磁盘文件交互了。
并且Mysql是关系型数据库，核心由表和索引组成，存储引擎还要负责表与索引的创建与持久化。

### Mysql存储引擎

````text
使用: SHOW ENGINES 命令可以查看Mysql所有的存储引擎。
````

#### InnoDB
InnoDB是Mysql最常用的存储引擎之一。

InnoDB主要特点如下:

- 采用聚集索引: InnoDB采用聚集索引(B+树)，即数据和索引存放在一个文件(.ibd)中。

- 自适应Hash: 网上有的资料说InnoDB引擎支持Hash，也有的说不支持。
Hash索引的查询(定位)效率是很高的，只是范围和有序查询是它的硬伤，抛开这点，
Hash索引的优势还是很大的。**InnoDB会自适应优化，如果判断建立Hash索引确实能够提高效率，
那么InnoDB将自己建立相关索引。**

参考: [58沈剑前辈的文章](https://zhuanlan.51cto.com/art/201910/604054.htm###)

- 支持事务: 在Mysql的所有引擎中，只有InnoDB支持事务，这也是它被广泛采用的原因之一。

- 既支持行锁也支持表锁

- 支持缓存: InnoDB支持缓存，既能缓存数据，也能缓存索引。

- 支持外键

- 支持全文索引: Mysql 5.6开始，InnoDB也支持全文索引。

#### MyISAM
MyISAM也是Mysql最常用的引擎之一。

MyISAM主要特点如下:

- 采用非聚集索引: MyISAM引擎采用的是非聚集索引(B+树)，即索引和数据分开存放，
**索引的叶子节点存放指向数据的指针。.MYD文件存放数据, .MYI文件存放索引**。

- 不支持事务: **MyISAM引擎不支持事务**，可以说这是它最大的缺点了。

- 只支持表锁: 相比InnoDB，MyISAM只支持表锁，所以在并发方面，MyISAM可能没有InnoDB那么出色

- 不支持外键

- 支持全文索引

- 保存表的行数: MyISAM保存表的行数，而InnoDB不保存，
所以使用 SELECT COUNT(*)查询，MyISAM比InnoDB要快。

#### MRG_MyISAM
MRG_MyISAM引擎也称为MERGE引擎。

**它实际上是一系列相同的MyISAM表的集合，创建MERGE表时，必须指定成员表。**
**对MERGE表的操作，就是对成员表的操作，对成员表的操作，也会反馈到MERGE表中。**

>假如对MERGE进行INSERT，其实是INSERT到MERGE表的成员表上，
>对成员表进行INSERT，结果也会体现到MERGE表上。

**MERGE引擎要求merge的表必须都是MyISAM引擎，
且这些表必须拥有相同数据类型的属性列，相同顺序的索引，
但是也允许每个表对应列和索引的名称不同。**

#### MEMORY
MEMORY内存引擎。

MEMORY主要特点如下:

- 不支持持久化机制: MEMORY表的数据是存放在内存中的，且MEMORY不支持持久化机制。
**也就是说一旦MYSQL服务器发生宕机等故障，那么数据是很可能丢失的。** 所以MEMORY适用于临时数据表。

- 只支持行锁，不支持表锁

- 默认采用Hash索引，但支持B树索引: HASH索引执行条件SQL非常快，但如果是范围查询，则需要全表扫描。

#### BLACKHOLE
BLACKHOLE 黑洞引擎。

它的主要特点如下:

- 不存储数据: 如它的名字一样:黑洞。 写入的数据都会被吞噬掉，只进不出，
不会存储数据，只有一个.sdi(.frm)文件，但是它会记录binlog。

- 分担主库压力: BLACKHOLE不存储数据就没有用了吗?当然不是。

>在普通的主从架构下，slave节点直接连接master节点进行binlog同步压力是比较大的，
>可以让BLACKHOLE引擎的数据库节点与master进行搭配，
>再让其他slave节点与BLACKHOLE节点进行同步，这样就降低了master的压力。


#### CSV
CSV文件存储引擎。

CSV主要特点如下:

- CSV引擎的表不支持主键和其他普通索引

- 所有字段必须为NOT NULL: CSV引擎的表要求所有字段必须非空。

- 逗号分隔列数据: CSV引擎如它的名字一样，以.csv文件存储数据，且列数据之间以逗号分割。
关于CSV文件还可以参考:[CSV文件](https://baike.baidu.com/item/CSV/10739)


#### ARCHIVE
ARCHIVE归档引擎，主要解决了冷数据存储问题。

ARCHIVE主要有以下特点:

- 占用空间小: 同样的数据，ARCHIVE引擎表占用的空间要比InnoDB小80%左右。

- 不支持删除和修改: ARCHIVE引擎的表不允许UPDATE和DELETE操作。

- 支持行锁

- 不支持索引: ARCHIVE引擎的表支持主键和自增，但是不支持普通索引。


#### FEDERATED
FEDERATED是一种特殊的存储引擎，在我的版本中(8.0.x)默认是不开启的。

FEDERATED引擎使得我们可以访问远程Mysql服务器中数据库的数据。

FEDERATED类型的表由两部分组成:
1. 远程表: 远程表的引擎可以是Mysql支持的任何类型，如:InnoDB,MyISAM等。
 
2. 本地存放的.frm文件，.frm文件是对表的定义，包含了指向远程表的字符串。
 
**FEDERATED引擎的本地表并不存放数据，当对本地表进行操作的时候，实际上是操作远程表。**

#### PERFORMANCE_SCHEMA
PERFORMANCE_SCHEMA系统存储引擎，**它是Mysql的一个特性,**
主要用来收集Mysql数据库在运行时的性能，
具体参考:[Mysql:PERFORMANCE_SCHEMA文档](https://dev.mysql.com/doc/refman/5.6/en/performance-schema.html)


---


### 事务

```text
事务并不是Mysql独有的，只是因为某些知识点以Mysql为示例，
所以便把它放在了Mysql之后。
```

#### 什么是事务?
**事务是一组原子性的操作序列，操作执行成功的结果使数据库从一种状态变成另一种状态，
且状态是持久的。**

#### 事务的四大特性(ACID)

![事务的四大特性](../img/database/mysql/事务的四大特性.png)

- **原子性(Atomicity)**: 原子性指事务是一组不可分割的操作，要么全部成功，
要么全部失败，不会出现一个操作成功，一个操作失败的情况。

- **一致性(Consistency)**: 一致性指事务对数据库操作前后，数据的完整性没有被破坏。

>如用户A给用户B转账，无论转账是否成功，A和B的财产总和是不变的。

- **隔离性(Isolation)**: 隔离性指事务与事务之间是相互独立的，互不干扰的，
一个事务的失败，不会影响另一个事务。

- **持久性(Durability)**: 持久性指事务对数据库的操作产生的影响应该是持久的，不会因为外部原因而发生改变。


#### DBMS中实现事务持久性的子系统是什么?

- 原子性：事务是一组不可分割的操作单元，这组单元要么同时成功要么同时失败（由DBMS的事务管理子系统来实现）；
- 一致性：事务前后的数据完整性要保持一致（由DBMS的完整性子系统执行测试任务）；
- 隔离性: 多个用户的事务之间不要相互影响，要相互隔离（由DBMS的并发控制子系统实现）；
- 持久性:一个事务一旦提交，那么它对数据库产生的影响就是永久的不可逆的，如果后面再回滚或者出异常，都不会影响已提交的事务（由DBMS的恢复管理子系统实现的）


#### 事务的隔离级别

1. 读未提交(READ UNCOMMITTED): 一个事务读取另一个事务未提交的数据。
**如果事务的隔离级别处于读未提交，那么可能产生脏读，换读和不可重复读等现象。**

2. 读已提交(READ COMMITTED): 一个事务读取另一个事务已提交的数据，**可以避免脏读，
但是又可能会出现不可重复读和幻读。**

3. 可重复读(REPEATABLE READ): 一个事务没有结束时，它对表中的同一条记录读取的结果都是相同的，
也就避免了不可重复读，**但还有可能发生幻读问题**。

4. 串行化(SERIALIZABLE): 串行化是最高的事务隔离级别，完全满足ACID四个特性。
**同一时间，数据库只能执行一个事务，事务之间完全互不干扰，这样就防止了脏读，幻读和不可重复读等问题。**

**PS:但是串行化相当于串行模式，效率是很低的，所以请慎用。**

| 事务的隔离级别 | 能否解决:脏读 | 能否解决:不可重复读 |  能否解决:幻读 |
| :----:       | :----:     | :----:           | :----: |
|   RU         |    ×       |    ×             |   ×    |
|   RC         |    √       |    ×             |   ×    |
|   RR         |    √       |    √             |   ×    |
|   S          |    √       |    √             |   √    |

#### 事务隔离级别引发的问题
- **脏读**: 脏读在事务隔离级别为读未提交的时候会出现。**脏读指读取到了一个事务还没有提交的数据。** 

>假设某张表的一个字段为money，有一条记录money的值为100。
>一个事务A对数据做了修改: money=120，但没有提交。
>此时，另一个事务B读取到了A修改但没有提交的数据 money=120，然后事务A回滚了，
>使得money仍然为原值100，那么事务B读到的money=120就是脏数据。

使用2个mysql客户端窗口模拟多线程事务导致的脏读:

![脏读](../img/database/mysql/脏读.png)

**设置事务隔离级别为读已提交可以避免脏读发生。**
````text
 SET SESSION TRANSACTION ISOLATION LEVEL READ COMMITTED;  
````

读已提交:

![读已提交&不可重复读](../img/database/mysql/读已提交&不可重复读.png)

可以看到，虽然读已提交解决了脏读，但是又出现了不可重复读问题。


- **不可重复读**: 不可重复读在事务隔离级别为读已提交时会出现。
**不可重复读指一个事务还没有结束时，多次读取同一条数据，可能读取的结果不一样。**

>假设某张表的一个字段为money，有一条记录money值为100。
>一个事务A读取了这条记录为100，此时，
>另一个事务B对这条记录做出了修改money=120,并提交了。
>当A再次读取money的时候，money为120 。

**设置事务隔离级别为可重复读可以避免不可重复读的问题发生。**

````text
SET SESSION TRANSACTION ISOLATION LEVEL REPEATABLE READ;
````

可重复读:

![可重复读](../img/database/mysql/可重复读.png)

**虽然可重复读避免了不可重复读问题，但幻读问题也随之而来。**

在说幻读之前,得先讲讲MVCC(Multi-Versioned Concurrency Control)机制。

**简单理解:这个机制保证了在某个时间，多个事务读取的是数据库的一个快照版本。**

关于MVCC机制可以看这篇文章:[MVCC](https://juejin.im/post/5c68a4056fb9a049e063e0ab)

再来说幻读:

- **幻读**: 了解了MVCC机制之后，再看幻读会觉得豁然开朗。
幻读在隔离级别为可重复读的时候会出现。
**可重复读虽然避免了不可重复读的问题，但是它也使得当前事务无法感知其他事务的操作。**

>假设事务A查询了一张表为空表，此时，另一个事务B插入了一条记录并提交了，
>当事务A也要插入记录的时候，却发生了主键冲突的错误，可当事务A再次查询的时候，仍然是空表呀。

幻读:
![幻读(快照读)](../img/database/mysql/幻读.png)

#### 快照读
解决幻读之前先看看快照读：
**快照读就是幻读。**

个人理解幻读(快照读)是MVCC机制出现的一种问题。

先来看看另一种情况: 当前读
  
![当前读](../img/database/mysql/当前读.png)

为什么上面处于可重复读级别的第一个事务在第一次读取之后，感知不到第二个事务的修改操作。
因为**在事务一开启后，事务会选择第一次SELECT(事务开启后的第一次SELECT)的结果作为快照，
此后的读取，都是读取的这个快照版本，即使其他事务更新了数据，
当前事务也认为这个快照是最新版本，所以读取的仍然是快照版本，数据当然一致。
这就揭露了，可重复读实际上是快照读。**

**那为什么会发生上面当前读的情况?**

**因为第一个事务开启后，并没有立刻SELECT，也就是在事务一内并不存在快照版本，
那么事务一就会选择记录的最新版本作为结果。**
最新的版本是什么时候?
是第二个事务修改数据并提交后，记录的版本也随之修改了，所以第一个事务能够感知到第二个事务的修改操作。

关于 <记录的最新版本>，还是和MVCC机制有关，这部分内容比较复杂，所以建议各位同学仔细阅读。

**避免幻读的有2种方式:串行化和加锁。**

看看加锁是如何解决幻读的:
![锁解决幻读](../img/database/mysql/锁解决幻读.png)

### 数据库锁

#### 数据库锁机制是什么
在编程语言中，有线程同步机制保证多线程对共享资源进行访问时的安全问题。

**在数据库中，也有事务锁同步机制，保证事务的一致性。**

#### 乐观锁和悲观锁
````text
锁从宏观上分为乐观锁和悲观锁。
````

- 乐观锁: 乐观锁一般是用户实现的一种锁机制。乐观锁机制对与共享数据很乐观，
认为任何时候都不会发生线程安全或事务一致性问题，所以不会给数据加锁。乐观锁适用于读多写少的应用。

- 悲观锁: 数据库锁基本都属于悲观锁。悲观锁认为在任何环境下，数据都有可能发生共享一致性问题，
所以每次读写数据的时候都会加锁。

#### 共享锁和独占锁(排他锁)
````text
按锁的操作可划分为共享锁和独占锁。
````

- 共享锁: 共享锁允许多个事务同时访问同一份共享数据。
**读锁就属于共享锁，多个事务可以同时对一份数据进行读操作。**

- 独占锁: 独占锁保证了在任何时候，只能有一个事务获取锁，其他事务只能等待获取锁的事务释放锁。
**写锁属于独占锁,一份数据同时只能被一个事务增删改。**

#### 行锁，表锁，页锁
```text
锁按粒度来划分，还可以分成行锁，表锁，页锁。
```

- 行锁: **行锁是最小粒度的一种锁，只针对当前事务操作的行加锁，即在当前事务范围内，
其他事务无法对当前事务操作的行进行修改，事务产生冲突的概率很小。**
行锁的加锁粒度最小，并发性高，但它的开销大，加锁慢，而且可能会出现死锁。

- 表锁:**表锁是粒度最大的一种锁，它对整张表加锁，即当在当前事务范围内，
其他事务无法对表做出修改，所以事务产生冲突的概率较大。**
表锁的粒度最大，并发性低，但它的实现较为简单，加锁很快，不会发生死锁。

- 页锁: 页锁是锁定粒度介于行锁和表锁中间的一种锁,并发性一般，可能会出现死锁。

#### 行锁基于索引
**在InnoDB中，行锁是基于索引实现的。
如果当前事务的操作没有基于索引，那么InnoDB将使用表锁。
这就意味着如果你使用一个SQL操作一条记录，但是这个条SQL的条件列并没有建立索引，
那么这条SQL即使操作一条记录，使用的也是表锁。**

行锁升级为表锁的一种情况:

![行锁基于索引](../img/database/mysql/行锁基于索引.png)

---

### Mysql Log日志

Mysql中有几种重要的日志文件，Mysql需要依赖这些日志文件完成非常重要的功能

#### binlog
二进制日志可以说是Mysql最重要的日志，它记录了所有的DDL和DML(SELECT和SHOW不会记录)语句。
**binlog的作用主要在于恢复记录和复制记录。**

#### redolog
**重做日志，它记录了事务的操作。**

它的作用是确保事务的持久性，防止因为外部原因，数据没来得及写入磁盘而丢失。
在Mysql启动时，会根据redolog重新执行事务操作，从而达到事务持久性。

**redolog在事务开启后就产生了，在事务的执行过程中，就被写入了redolog。**
redolog日志大小是固定的，当事务执行完后，数据落盘后，redolog就会被覆盖掉。

#### undolog
回滚日志,它记录了事务开始前数据的一个版本状态，如果事务在记录到redolog时，
就出现了意外，就可以将数据回滚到事务之前的这个状态。

---

### Mysql优化

#### Explain执行计划

>Explain是Mysql的优化神器，它可以对一条Query SQL进行分析，
>并输出SQL的详细信息，以便于优化SQL。

下面是Explain解析一条SELECT的例子:

![Explain执行计划](../img/database/mysql/Explain执行计划.png)

EXPLAIN输出的属性如下:

- id: id是SELECT查询的序列号，表示一条SELECT或SELECT中子查询的执行顺序。主要有2种情况:
 
  - 如果id相同，可以被认为是同一分组，执行顺序，从上到下。
  - 如果id不同，id值越大，那么越先执行。


- **select_type**: select_type是为了区分简单查询，复杂查询，子查询等查询类型。
select_type主要有如下值:
  
  - SIMPLE: SIMPLE代表简单查询，SELECT中不包含子查询或联合查询等复杂查询。
  
  - SUBQUERY: SUBQUERY表示子查询部分。
  
  - PRIMARY: PRIMARY表示最外层查询，如果一个SELECT中包含子查询，
             那么最外层的查询就是PRIMARY。
  
  - DERIVED: DERIVED代表查询的结果被放入临时表中。
             如FROM 语句后跟着一个 SELECT ，那么SELECT的结果就可能被放入临时表中。
  
  - UNION: UNION代表联合查询，也就是UNION后的SELECT。
  
  - UNION RESULT: UNION RESULT代表联合查询的结果。
  
- table: table表示查询的表。

- partitions: partition代表查询匹配的分区，对于非分区表为NULL。

- **type**: 查询类型，是衡量SQL的一个重要的指标。
        一般来说，至少要达到range标准，最好达到ref。
        它有如下值：
    
  - SYSTEM: SYSTEM代表表只有一条记录，他是CONST类型的一个特例。
  
  - CONST: CONST表示表只最多只有一个匹配行，只用读一次，
           因此优化器可以视查询结果为一个常量。
  
  - EQ_REF: EQ_REF代表唯一性索引扫描。比如以 unique key索引或主键作为条件，
            这2种索引都是唯一的，表中只有一条记录与之匹配。
  
  - REF: REF代表非唯一索引匹配，返回匹配条件的所有行。
         比如WHERE条件的列有索引，经过匹配后，发现有多条符合条件的记录。
  
  - RANGE: RANGE表示范围扫描。如使用>,<,BETWWEN等条件。
  
  - INDEX: INDEX代表全表扫描，不过它与ALL的区别在于，
           INDEX是在索引列上进行全表扫描，一般要比ALL快。
  
  - ALL: ALL代表全表扫描，效率最低。
  
- possible_keys: poosible keys代表查询涉及到的字段如果有索引会被列出来，
                 但不一定使用。

- key: key代表查询实际使用到的索引，如果为NULL，则没有使用索引。

- key_len: key_len表示使用索引的实际长度。

- ref: ref表示与索引比较的列或这常量。
       假设 WHERE以主键作为条件 id = 10,那么ref显示的就是const，
       因为主键为10，就是一个常量。

- rows: rows代表查询优化器估算查询结果集要扫描的行数，
        也就是执行SELECT预计需要扫描的行数。

- filtered: filtered代表SELECT执行时过滤掉的记录与rows的百分比。
            filtered 显示的百分比 与 rows 的乘积就是查询时过滤掉的行数。

- EXTRA: 显示SQL执行时的附加信息


#### 开启慢查询日志

**慢查询用于记录查询超过某个临界值的SQL。**

使用:

````text
SHOW VARIABLES LIKE 'SLOW_QUERY_LOG';
````
查看慢查询是否开启，如果显示OFF，那么执行:


````text
set GLOBAL SLOW_QUERY_LOG = on 
````
开启慢查询日志。

---

使用:
````text
SHOW VARIABLES LIKE 'LONG_QUERY_TIME';
````
查看慢查询临界值,单位: 秒。

使用:
````text
SET LONG_QUERY_TIME=2
````
设置慢查询临界值。

**开启慢查询后，会在mysql的数据目录下产生xxx-slow.log慢查询日志文件，
一旦某条SQL超过了临界值，就会被记录到慢查询日志文件中。**


#### 为什么要求字段尽量设置为NOT NULL?
因为Mysql难以优化可以为空的字段，**一旦字段被建立了索引，
那么就需要额外的空间来存储此当前行记录是否为NULL的标识。**

#### 为什么主键尽量设置成有序和整型?
这个问题其实在索引章节就说过了，索引的结构是B+树，B+树最大的优点就是顺序查找，
有序的主键当然有利于查找，像UUID等这种长字符串，连排序都难以解决。


---


### Mysql数据类型

#### UTF8和UTF8MB4

在mysql中，UTF8编码最多能存放3个字节的数据，也就是说几乎可以存放所有的中文汉字了。
但是如果遇到像emoji这种特殊的字符，那UTF8就不够用了。
在mysql5.5.3版本后，mysql加入了一种新的字符: UTF8MB4,他是UTF8的超集，
最多可以支持4个字节的数据，所以解决了UTF8兼容性的问题。

#### CHAR 和 VARCHAR
CHAR是固定长度的字符串,VARCHAR是可变的字符串。

**mysql5.0版本以上，CHAR(M)和VARCHAR(M)的长度M不再指字节长度，
而单纯的就是指长度。**

如CHAR(1)和VARCHAR(1), 既可以存放1个中文字符，也可以存放1一个英文字符，只不过它们底层的字节长度不同。
一个中文字符约等于3个字节，所以CHAR(1)如果存放一个中文字符，那么mysql底层的字节长度将为3。
(VARCHAR的实际最大长度还得看表的字符编码,UTF8最大只支持3个字节，UTF8MB4支持4个字节)

它们的主要区别如下:
- 长度上限不同: CHAR长度的上限为255个字节(约85个汉字),
   VARCHAR长度的上限为65535个字节(约21845个汉字)(mysql 5.0 以上)，和text相同。

- 占用空间不同: 使用CHAR 作为类型的话，无论该字段字符的长度是否小于指定长度，都会占用指定长度的空间。
  而VARCHAR则是根据字符的长度来决定占用的空间，这就是可变长字符串的好处。
              
- 是否删除字符串末尾的空字符串: **如果字符串末尾有空格字符，CHAR则会删除其末尾的空格，
  而VARCHAR不会删除字符串末尾的空格。**

- 效率问题: 由于VARCHAR是可变长的，如果对字符串进行更改的时候，
  那么也会修改其相应的空间，这在效率上就没有CHAR那么高效了。
          
     
#### TIMESTAMP 和 DATETIME

TIMESTAMP和DATETIME都是用于表示时间的类型。

它们主要有如下区别:

- **占用空间不同**: TIMESTAMP占用4个字节；DATETIME占用8个字节,因此TIMESTAMP更加节省空间。

- **时间范围不同**: TIMESTAMP表示 1970 - 2038年；DATETIME表示: 1000 - 9999 年。

- **是否受时区影响**: TIMESTAMP的时间会受当前Mysql的时区影响；
  而DATETIME则不受影响，存进去什么时间，拿出来就什么时间。


- **默认值不同**: TIMESTAMP字段的值如果为NULL，那么将会自动更新到当前时间；
  DATETIME存进去NULL，就默认为NULL。

#### 如何在TIMESTAMP和DATETIME之中选择?
如果你想让一个时间字段表示的范围更大，且不受系统时区影响，那么建议选择DATETIME。
其他情况考虑TIMESTAMP吧。



### SQL Practice
以下是关于SQL的练习，建议各位同学先用手写，写不出来再在电脑上写，
因为手写SQL可以让你加深对于SQL理解。

**纸上得来终觉浅，觉知此事要躬行。**

#### 1
有2张表tb1和tb2如下:

tb1 :

| bh1 | num1 |
| :---:| :---: |
| 1    |  100    |
| 2    | 200  |
| 3    | 300  |

tb2 :

| bh1 | num2 |
| :---:| :---: |
| 4    |  400    |
| 5    | 500  |
| 6    | 600  |

给定一个结果表: result

| bh | num |
| :---:| :---: |
| 1    |  100    |
| 2    | 200  |
| 3    | 300  |
| 4    | 400  |
| 5    | 500  |
| 6    | 600  |

请编写一条SQL，从tb1和tb2中查询到如result表的结果。

#### 2

有2张表tb1和tb2如下:

tb1 :

| bh1 | num1   |    xb1 |
| :---:| :---: |  :---: |
| 1    |  100  |   0   |
| 3    | 300  |    1   |
| 2    | 200  |    0   |

tb2 :

| bh1 | num2 |    xb2 |
| :---:| :---: | :---: |
| 4    |  400  |  1   |
| 6    | 600  |   1   |
| 5    | 500  |   0   |

给定一个结果表: result

| bh   |   num |   xb    |    
| :---:| :---: |  :---:  |
| 1    |  100  |   女    |
| 2    | 200  |    女    |
| 3    | 300  |    男    |
| 4    | 400  |    男    |
| 5    | 500  |    女    |
| 6    | 600  |    男    |

请编写一条SQL，从tb1和tb2中查询到如result表的结果。