# Java JDBC

## 一、介绍

Java数据库连接，（Java Database Connectivity，简称JDBC）是[Java语言](https://baike.baidu.com/item/Java语言)中用来规范客户端程序如何来访问数据库的[应用程序接口](https://baike.baidu.com/item/应用程序接口/10418844)，提供了诸如查询和更新数据库中数据的方法。JDBC也是Sun Microsystems的商标。我们通常说的JDBC是面向关系型数据库的。

### 1.基本概念

- 驱动：驱动，[计算机软件](https://baike.baidu.com/item/计算机软件/223688)术语，是指驱动计算机里软件的[程序](https://baike.baidu.com/item/程序/71525)。驱动程序全称设备驱动程序，是添加到[操作系统](https://baike.baidu.com/item/操作系统/192)中的特殊程序，其中包含有关硬件设备的信息此信息能够使计算机与相应的设备进行通信。
- 数据库驱动：使应用程序能够和数据库进行通信。

### 2.相关包

Java.sql、Javax.sql(默认有)、导入数据库驱动包

### 3.JDBC操作

（1）准备测试数据

```sql
-- 创建测试数据库
CREATE TABLE `users`(
	id INT PRIMARY KEY,
	NAME VARCHAR(40),
	PASSWORD VARCHAR(40),
	email VARCHAR(60),
	birthday DATE
);

-- 插入测试数据
INSERT INTO `users`(id,NAME,PASSWORD,email,birthday)
VALUES(1,zhansan,123456,zs@sina.com,1980-12-04),
(2,lisi,123456,lisi@sina.com,1981-12-04),
(3,wangwu,123456,wangwu@sina.com,1979-12-04)
```

（2）导入数据库驱动

