---
product: campaign
title: 切换到Unicode
description: 切换到Unicode
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 切换到Unicode{#switching-to-unicode}



对于Linux/PostgreSQL中的现有&#x200B;**prod**&#x200B;实例，切换到Unicode的步骤如下：

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

1. 还原数据库：

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. 更新指示数据库为Unicode的选项：

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

   在与数据库标识符(**databaseId**)相关的值前添加&#x200B;**u**&#x200B;字符：

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

1. 确认交换机。 为此，请通过Adobe Campaign控制台连接并：

   * 检查数据是否正确显示，特别是重音字符：
   * 启动投放并检查跟踪检索是否有效。
