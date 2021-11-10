# Java JDBC

## 一、介绍

Java数据库连接，（Java Database Connectivity，简称JDBC）是[Java语言](https://baike.baidu.com/item/Java语言)中用来规范客户端程序如何来访问数据库的[应用程序接口](https://baike.baidu.com/item/应用程序接口/10418844)，提供了诸如查询和更新数据库中数据的方法。JDBC也是Sun Microsystems的商标。我们通常说的JDBC是面向关系型数据库的。

### 1.1 基本概念

- 驱动：驱动，[计算机软件](https://baike.baidu.com/item/计算机软件/223688)术语，是指驱动计算机里软件的[程序](https://baike.baidu.com/item/程序/71525)。驱动程序全称设备驱动程序，是添加到[操作系统](https://baike.baidu.com/item/操作系统/192)中的特殊程序，其中包含有关硬件设备的信息此信息能够使计算机与相应的设备进行通信。
- 数据库驱动：使应用程序能够和数据库进行通信。

### 1.2 相关包

Java.sql、Javax.sql(默认有)、导入数据库驱动包

## 二、使用

### 2.1 JDBC操作

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

下载数据库驱动，导入lib

（3）编写测试类

```Java
package com.xu.jdbc;


import java.sql.*;

// 一个JDBC测试程序
public class JdbcFirst {	
    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        // 1.加载驱动，固定写法加载驱动	
        Class.forName("com.mysql.jdbc.Driver");
        // 2.用户信息
        String url = "jdbc:mysql://1.117.228.214:3306/learn_sql?useUnicode=true&characterEncoding=utf8&useSSL=false";
        String username = "learn_sql";
        String pasword = "3dkrEwCwze7r3ECS";
        // 3.获取连接
        Connection conn = DriverManager.getConnection(url, username, pasword);
        // 4.执行sql
        Statement statement = conn.createStatement();
        String sql = "select * from users";
        ResultSet res = statement.executeQuery(sql);

        while (res.next()) {
            System.out.println("id=" + res.getObject("id"));
            System.out.println("name=" + res.getObject("name"));
            System.out.println("password=" + res.getObject("password"));
            System.out.println("email=" + res.getObject("email"));
            System.out.println("birthday=" + res.getObject("birthday"));
        }

        // 5.释放连接
        res.close();
        statement.cancel();
        conn.close();
    }

}

```

#### 步骤总结

1.加载驱动

2.连接数据库DriverManager

3.获取sql执行对象Statement	

4.获取返回的结果集ResultSet

5.释放连接

#### Statement 对象

增删改-excuteUpdate()

查-excuteQuery()

#### sql注入问题

sql存在问题，导致数据库泄露。

#### prepareStatement sql预编译防止sql注入

