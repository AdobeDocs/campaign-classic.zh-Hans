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
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 5%

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

