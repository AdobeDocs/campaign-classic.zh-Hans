---
solution: Campaign Classic
product: campaign
title: 连接阈值
description: 连接阈值
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---


# 连接阈值{#connection-thresholds}

对于负载较重的服务器，可能会超出连接阈值。 在任何事件，找出原因都很有用。

有三种不同的阈值：

1. 在Web服务器中配置的Web连接阈值。 要修改它，请与系统管理员联系。
1. 数据库连接阈值。 要修改它，请与数据库管理员联系。
1. Adobe Campaign连接阈值，在以下两个位置可用：

   * Tomcat侧：所有查询实际上都到达了Adobe CampaignTomcat客户端。

      此阈值在nl6/tomcat-8/conf/server.xml文件 **中配** 置。 maxThreads **属性** 允许您增加一次处理的查询数的阈值。 例如，可以将其更改为250。

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

   * 数据库：一组进程在数据库上同时打开的所有连接。

      此阈值在文件nl6/conf/serverConf.xml中 **配置**。 位于 **数据源** 池中的maxCnx **属性** ，可让您提高同时处理的查询的阈值。

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

