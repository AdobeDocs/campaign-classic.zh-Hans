---
product: campaign
title: 切换到Unicode
description: 切换到Unicode
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 5%

---

# 切换到Unicode{#switching-to-unicode}



对于现有 **prod** 在Linux/PostgreSQL实例中，切换到unicode的步骤如下所示：

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

   添加 **u** 与数据库标识符相关的值前面的字符(**databaseId**)：

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
