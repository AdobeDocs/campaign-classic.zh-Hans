---
product: campaign
title: 连接阈值
description: 连接阈值
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 连接阈值{#connection-thresholds}



对于重载服务器，可能会超过连接阈值。 无论如何，查明原因都很有用。

有三种不同的阈值：

* 此 **Web连接阈值**，已在Web服务器中配置。 要修改它，请联系您的系统管理员。

* 此 **数据库连接阈值**. 要修改它，请与数据库管理员联系。

* 此 **Adobe Campaign连接阈值**，可在以下两个位置使用：

   * **Tomcat** side：所有查询实际到达了Adobe Campaign Tomcat客户端。

      此阈值配置于 **nl6/tomcat-8/conf/server.xml** 文件。 此 **maxThreads** 通过属性，可增加一次处理的查询数量的阈值。 例如，可以将其更改为250。

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

   * **数据库**：由进程在数据库上同时打开的所有连接集。

      此阈值在文件中配置 **nl6/conf/serverConf.xml**. 此 **maxCnx** 属性位于 **数据源池** 可让您提高同时处理的查询的阈值。

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
