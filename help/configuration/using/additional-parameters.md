---
title: 其他参数
seo-title: 其他参数
description: 其他参数
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 其他参数{#additional-parameters}

## 参数的定义 {#definition-of-parameters}

您的Adobe Campaign平台提供两个TRANSACTION类型的Web跟踪参数作为标准：

* **amount**:表示交易金额，
* **文章**:表示事务中的项数。

这些参数在 **nms:webTrackingLog架构中定义** ，是报告中看到的一些指示符。

要定义其他参数，必须扩展此架构。

**示例**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

您可以通过配置跟踪日志列表（分发或收件人）来显示这些参数的值。

## 重定向服务器配置 {#redirection-server-configuration}

在服务器配置中，您可以定义Web跟踪参数要考虑的最大字符数。

>[!CAUTION]
>
>增加要考虑的最大字符数可能会影响平台的Web跟踪性能。

为此，请修改 **serverConf.xml文件中元** 素的webTrackingParamSize **`<trackinglogd>`****属性** 。 此文件保存在Adobe Campaign安 **装目录** 的conf子目录中。

**示例**:

默认值为64个字符。 此值允许您考虑 **amount** 和 **article** (&quot;amount=xxxxxxxxx&amp;article=xxxxxxx&quot;)标准参数。

通过考虑上述扩展架构示例中指示的两个参数（名称大小+值大小），您可以修改配置以考虑100个字符(“amount=xxxxxxxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxxxxx&amp;code=xxxxx”)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改配置后，您必须：

* 停止承载重定向模块（Apache、IIS等）的Web服务器，
* 停止Adobe Campaign服务器：在 **Windows中停止nlserver6** ，在 **Linux中停止/etc/init.d** /nlserver6,
* 在Linux中，使用 **ipcrm命令删除共享内存段** ,
* 重新启动Adobe Campaign服务器：在 **Windows中启动nlserver6** ，在 **Linux中启动/etc/init.d/nlserver6** ,
* 重新启动Web服务器。

**示例**:考虑Linux下的配置。

```
adobe@selma:~$ /etc/init.d/nlserver6 stop
adobe@selma:~$ /etc/init.d/apache stop
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ /etc/init.d/nlserver6 start
adobe@selma:~$ /etc/init.d/apache start
```

>[!NOTE]
>
>对于Linux，如果增加 **webTrackingParamSize** 或 **** maxSharedLogs参数的大小，则可能需要增加共享内存(SHM)的大小。

