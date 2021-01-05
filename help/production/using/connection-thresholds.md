---
solution: Campaign Classic
product: campaign
title: 连接阈值
description: 连接阈值
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---


# 连接阈值{#connection-thresholds}

对于负载较重的服务器，可能会超出连接阈值。 在任何事件，找出原因都很有用。

有三种不同的阈值：

* 在Web服务器中配置的&#x200B;**Web连接阈值**。 要修改它，请与系统管理员联系。

* **数据库连接阈值**。 要修改它，请与数据库管理员联系。

* **Adobe Campaign连接阈值**，可在以下两个位置使用：

   * **汤** 卡赛德：所有查询实际上都到达了Adobe CampaignTomcat客户端。

      此阈值在&#x200B;**nl6/tomcat-8/conf/server.xml**&#x200B;文件中配置。 通过&#x200B;**maxThreads**&#x200B;属性，可以增加每次处理的查询数的阈值。 例如，可以将其更改为250。

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * **数据库**:一组进程在数据库上同时打开的所有连接。

      此阈值在文件&#x200B;**nl6/conf/serverConf.xml**&#x200B;中配置。 位于&#x200B;**数据源池**&#x200B;的&#x200B;**maxCnx**&#x200B;属性允许您增加同时处理的查询的阈值。

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```

