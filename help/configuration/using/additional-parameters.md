---
product: campaign
title: 其他Web跟踪参数
description: 了解有关Web跟踪参数的更多信息
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---

# 其他参数{#additional-parameters}

## 参数{#definition-of-parameters}的定义

您的Adobe Campaign平台提供两个TRANSACTION类型的Web跟踪参数作为标准：

* **金额**:表示交易金额，
* **文章**:表示交易记录中的项目数。

这些参数在&#x200B;**nms:webTrackingLog**&#x200B;模式中定义，是报告中看到的一些指标。

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

您可以通过配置（投放或收件人）的跟踪日志列表来显示这些参数的值。

## 重定向服务器配置{#redirection-server-configuration}

在服务器配置中，您可以定义Web跟踪参数要考虑的最大字符数。

>[!IMPORTANT]
>
>增加需要考虑的最大字符数可能会影响平台的Web跟踪性能。

为此，请在&#x200B;**serverConf.xml**&#x200B;文件中修改&#x200B;**`<trackinglogd>`**&#x200B;元素的&#x200B;**webTrackingParamSize**&#x200B;属性。 此文件保存在Adobe Campaign安装目录的&#x200B;**conf**&#x200B;子目录中。

**示例**:

默认值为64个字符。 此值允许您考虑&#x200B;**amount**&#x200B;和&#x200B;**article**(&quot;amount=xxxxxxx&amp;article=xxxxxxxx&quot;)标准参数。

通过考虑上述扩展架构示例中指示的两个参数（名称大小+值大小），您可以修改配置以考虑100个字符(“amount=xxxxxxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxxxx&amp;code=xxxxx”)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改配置后，您必须：

* 停止承载重定向模块（Apache、IIS等）的Web服务器，
* 停止Adobe Campaign服务器：**net stop nlserver6**（在Windows中），在Linux中， **/etc/init.d/nlserver6 stop**

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）：**systemctl停止nlserver**

* 在Linux中，使用&#x200B;**ipcrm**&#x200B;命令删除共享内存区段，
* 重新启动Adobe Campaign服务器：**net start nlserver6**（在Windows中），在Linux中， **/etc/init.d/nlserver6 start**

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）：**systemctl启动nlserver**

* 重新启动Web服务器。

**示例**:考虑Linux下的配置。

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
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
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>对于Linux，如果您增加&#x200B;**webTrackingParamSize**&#x200B;或&#x200B;**maxSharedLogs**&#x200B;参数的大小，则可能需要增加共享内存(SHM)的大小。
