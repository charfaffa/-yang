在客户端的连接命名
mysql [-h 127.0.0.1] [-P 3306] -u root -p

-u, --user=name 指定用户名
-p, --password[=name] 指定密码
-h, --host=name 指定服务器IP或域名
-P, --port=# 指定连接端口


# 操作
1. 上下键可以切换到我们之前执行过的语句
2. 不要用utf-8，用utf-8mb

# sql语言
SQL语言是结构化查询语言，英文是sturctured query language
# 通用语言
    > 1. sql不区分大小写，但关键字建议大写
    > 2. 每一句sql语言以分号(;)结尾，可以换行写，但是句尾必须有分号
    > 3. 可以用空格和缩进增加代码的可读性
## 注释
1. 单行注释 用(--)或(#)后面加注释内容
2. 多行注释 用(/*注释内容*/)

# sql分DDL、DML、DQL、DCL
1. ## DDL命令
    ### 1.1数据库操作
   ```sql
    1 show databases； 
     #查询当前所有数据库  
     #末尾有s
    2 create database [if not exists] 数据库名 [default charset 字符集] [collate 排序规则] ;
    #创建数据库
    #字符集要用utf-8mf4 #不能创建两个同名数据库
    #没有s
    3 drop [if exists]database 数据库名
    #删除数据库
    4 use 数据库名；
    #切换数据库
    5 select database()
    #查看当前数据库
    #后面是有括号的
    ```
    ### 1.2 表操作
    #### 1.2.1 查询与创建
    ```sql
    1. show tables;
    #查询当前数据库中所有表
    2. desc 表名；
    #查询指定表名的表结构
    3. show create table 表名；
    #查询建表语句
    4. create table 表名(
        字段1 字段类型 [comment 字段注释],
        字段2 字段类型 [comment 字段注释],
        ...
        字段n 字段类型 [comment 字段注释],
    ) [comment 表注释]；

    ```
    #### 1.2.2 修改
    ```sql
    5. alter table 表名 add 字段名 字段类型[comment 注释]；
    #添加字段
    6. alter table 表名 mondiy 字段名 字段类型；
    #修改字段数据类型
    7. alter table 表名 change 旧字段名 新字段名 类型（长度）
    #修改原有的字段名和数据类型
    8. alter table 表名 rename to 新表名
    #修改表名
    9. alter table 表名 drop 字段名
    #删除指定字段
    ```
    #### 1.2.3 删除
    ```sql
    1.drop table [if exists] 表名;
    #删除表，如果表存在
    10. truncate table 表名
    #删除表
```

    ### 1.3 数据类型(三种)
    ```sql
    太多了，写出一些常用的
    11. 数值类型
    unsigned #如果正数或负数就在后面加个unsigned
        tinyint #100以下的数据范围
        int #一般就用这个
        float #浮点数
    12. 文本类型
        char #定长字符串
        varchar #变长字符串
        text #一般用这个
    13. 日期类型
        date #日期  
        #范围：1000-01-01 至 9999-12-31  
        #格式：yyyy-mm-dd
        time #时间
        #范围：-838:59:59 至 838:59:59
        #格式：hh：mm：ss
        year #年份
        格式：yyyy
        datetime #混合时间
        范围：1000-01-01 00:00:00 至 9999-12-31 23:59:59
        格式中介用空格
    ```
 2. ### DML(数据操作语言)
    #### 2.1添加数据
    ```sql
    1.insert into 表名 (字段1，字段2....) values(值1，值2，..)
    #给指定字段添加值
    2.insert into 表名 valuse(值1，值2...)
    #给所有字段添加值
    3.可以批量添加，valuse(值1，值2，...) (值1，值2，..)
    ```
    #### 2.2修改数据
    ```sql
    1. update 表名 set 字段1=值1，字段2=值2，...[where 条件]
    #例如 将id为1的数据name修改为itheima
    update 表名 set name=itheima where id=1
    ```
    #### 2.3删除数据
    ```sql
    2. delete form 表名 [where 条件]
    #删除指定条件的数据
    3. delete form 表名
    ```
2. ### DQL(数据查询语言)
   #### 3.1基本查询
   一般在开发中不使用通配符*，但是可以用
   不重复也是在查询的结果中去重，不会影响原数据。
   聚合函数count(*)指所有的数据条有多少个。
   ```sql
   select 字段1，字段2，···· from 表名
   #查询指定字段
   select * from 表名
   #查询全部字段，但不建议使用
   select 字段1 [as 别名]，字段2[as 别名],···· from 表名；
   #给字段重新命名 as可以省略
   select distinct 字段1 form 表名；
   ```
   #### 3.2条件查询
   ```sql
   select 字段1，字段2，··· from 表名 where 条件;
   ```
   条件；
   #模糊匹配(_匹配单个字符, %匹配任意个字符)
   有比较运算符合条件运算符。

   |比较运算符|功能|
   | ---- | ---|
   |between...and...|在某个范围之内(含最小、最大值)|
   |in(...)|在in之后的列表值，多选一|
   |link 占位符|_匹配单个字符, %匹配任意个字符|

   #### 3.3聚合函数
   常见的聚合函数
   |函数|功能|
   |---|----|
   |count()|统计个数|
   |max()|最大值|
   |min()|最小值|
   |sum()|求和|
   |avg()|求平均值|

   语法：
   ```sql
   select 聚合函数（字段列表） from 表名;
   #null不参与所有聚合函数的计算
   可以使用通配符
   ```
   #### 3.4 分组查询
   语法：
   ```sql
   select 字段列表 from 表名 [where 条件] group by 分组字段 [having 分组后过滤条件];
   where 不能对聚合函数进行判断
   having 在where之后进行判断
   ```
   #### 3.5 排序查询
   语法：
   ```sql
   select 字段列表 from 表名 order by 字段1 排序方式，字段2 排序方式
   #排序方式；
   asc :升序排序（默认值）
   desc ：降序排序
   ```

#### 3.5分页查询
   ```sql
   select 字段列表 from 表名 limit 起始索引，查询记录数;
   ```

   ### 4.DQL
   管理用户，控制用户权限
   ```sql
   #查询有哪些用户
   select * from mysql.user
   #创建用户
   create user '用户名'@'主机名' identified by '密码'
   #修改密码
   alter user '用户名'@'主机名' identified with mysql_native_password by '新密码'
   #删除用户
   drop user '用户名'@'主机名'

   

   



   



    


   
    












