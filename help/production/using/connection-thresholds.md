---
product: campaign
title: 连接阈值
description: 连接阈值
feature: Monitoring
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# 连接阈值{#connection-thresholds}



对于重载服务器，可能会超过连接阈值。 无论如何，查明原因会很有用。

有三种不同的阈值：

* 此 **Web连接阈值**，已在Web服务器中配置。 要修改它，请与系统管理员联系。

* 此 **数据库连接阈值**. 要修改它，请与数据库管理员联系。

* 此 **Adobe Campaign连接阈值**，可在以下两个位置使用：

   * **Tomcat** 侧：所有查询实际都到达了Adobe Campaign Tomcat客户端。

     此阈值配置于 **nl6/tomcat-8/conf/server.xml** 文件。 此 **maxThreads** 属性允许您提高一次处理的查询数量的阈值。 例如，可以将其更改为250。

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
