---
title: 连接阈值
seo-title: 连接阈值
description: 连接阈值
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 连接阈值{#connection-thresholds}

对于负载较重的服务器，可能会超出连接阈值。 无论如何，找出原因都很有用。

有三种不同的阈值：

1. Web连接阈值，在Web服务器中配置。 要修改它，请与系统管理员联系。
1. 数据库连接阈值。 要修改它，请与数据库管理员联系。
1. Adobe Campaign连接阈值有两个位置：

   * Tomcat侧：实际到达Adobe Campaign Tomcat客户端的所有查询。

      此阈值在nl6/tomcat-7/conf/server.xml文件中 **配置** 。 使用 **maxThreads** 属性，您可以增加一次处理的查询数的阈值。 例如，可以将其更改为250。

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

   * 数据库：一个进程在数据库上同时打开的所有连接集。

      此阈值在文件nl6/conf/serverConf.xml中 **配置**。 位于 **数据源池中的** maxCnx **属性** ，可让您增加同时处理的查询的阈值。

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

