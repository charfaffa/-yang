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
    #查询指定数据库库的表结构
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
    1. delete form 表名 [where 条件]
    #删除指定条件的数据
    2. delete form 表名
    ```
    

    


   
    












