
## 文件结构

InnoDB 是索引组织表，即：索引即数据。

    1. 聚集索引：包含一整行的记录（主键值和整行记录）；
    2. 非聚集索引：包含非聚集索引的键值和主键值；
    3. 根据非聚集索引查找整行记录时，需要根据主键值，进行一次额外的书签查找。
    4. 书签查找的算法：二分查找
### 表空间
    即：文件ibdata
    1. 是否每个表生成一个文件由参数：innodb_file_per_table控制。
    2. 每张表的表空间内存放的只是数据、索引和插入缓冲Bitmap；
    3. 回滚信息、插入缓冲索引页、系统事务日志、写缓冲等信息，仍然存放在共享表空间。
    
### 段[segment]
    包括各种Leaf node segment、Non-Leaf node segment、Rollback segment等
    数据段：Leaf node segment;
    索引段：Non-Leaf node segment
### 区[extern]
    由连续的页组成，每个区的大小是1M，在默认情况下，InnoDB存储引擎的页大小为16K，即64个连续的页。
### 页[page]
    常见的页：数据页、undo页、系统页、事务数据页、插入缓冲页等
### 行[row]
    每行记录都会额外的添加2[或3]列
    1. tx_id 事务id用来实现行级锁
    2. rollback_pointer即：undo pointer 用来实现mvcc
    3. row_id 在记录没有创建主键或者没有唯一索引时，自动创建作为主键值。

