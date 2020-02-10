---
title: 切换到Unicode
seo-title: 切换到Unicode
description: 切换到Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 切换到Unicode{#switching-to-unicode}

对于Linux/ **Postgre** SQL中的现有prod实例，切换到unicode的步骤如下：

1. 停止写入数据库的进程：

   ```
   su - neolane
   nlserver shutdown
   ```

1. 转储数据库：

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. 创建Unicode数据库：

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. 恢复数据库：

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. 更新表示数据库为Unicode的选项：

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. 在跟踪服务器上：

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   在与数 **据库标识符** (databaseId)相关的值前添加u **字符**:

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. 在调用数据库的服务器上：

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   修改数据库引用：

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. 重新启动所有计算机：

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. 确认交换机。 为此，请通过Adobe Campaign控制台进行连接，并：

   * 检查数据显示是否正确，尤其是突出显示的字符：
   * 启动交付并检查跟踪检索是否有效。

