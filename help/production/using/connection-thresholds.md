---
product: campaign
title: 连接阈值
description: 连接阈值
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 连接阈值{#connection-thresholds}

![](../../assets/v7-only.svg)

对于负载较重的服务器，可能会超出连接阈值。 无论如何，找出原因都很有用。

有三个不同的阈值：

* 的 **Web连接阈值**，在web服务器中配置。 要修改它，请与系统管理员联系。

* 的 **数据库连接阈值**. 要修改它，请与数据库管理员联系。

* 的 **Adobe Campaign连接阈值**，分为两个位置：

   * **Tomcat** 侧：所有查询都实际到达Adobe Campaign Tomcat客户端。

      此阈值在 **nl6/tomcat-8/conf/server.xml** 文件。 的 **maxThreads** 属性允许您增加一次处理的查询数的阈值。 例如，可以将其更改为250。

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

   * **数据库**:一组由进程在数据库上同时打开的所有连接。

      此阈值在文件中配置 **nl6/conf/serverConf.xml**. 的 **maxCnx** 位于 **数据源池** 允许您增加同时处理的查询的阈值。

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
