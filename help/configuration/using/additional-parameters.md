---
product: campaign
title: 其他Web跟踪参数
description: 了解有关Web跟踪参数的更多信息
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 其他Web跟踪参数{#additional-parameters}

## 参数的定义 {#definition-of-parameters}

您的Adobe Campaign平台提供两个TRANSACTION类型的Web跟踪参数作为标准：

* **数量**：表示交易金额，
* **文章**：表示交易记录的项数。

这些参数在 **nms：webTrackingLog** 架构，和是报表中看到的一些指标。

要定义其他参数，必须扩展此架构。

**示例**：

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

您可以通过配置（投放或收件人的）跟踪日志列表来显示这些参数的值。

## 重定向服务器配置 {#redirection-server-configuration}

在服务器配置中，您可以定义用于Web跟踪参数的最大字符数。

>[!IMPORTANT]
>
>增加要考虑的最大字符数可能会影响平台的Web跟踪性能。

为此，请修改 **webTrackingParamSize** 的属性 **`<trackinglogd>`** 中的元素 **serverConf.xml** 文件。 此文件保存在 **会议** Adobe Campaign安装目录的子目录。

**示例**：

默认值为64个字符。 通过此值，可将 **数量** 和 **文章** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;)标准参数。

通过考虑上述扩展架构示例中指示的两个参数（名称大小+值大小），您可以修改配置以考虑100个字符(&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxx&quot;)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改配置后，您必须：

* 停止托管重定向模块的Web服务器（Apache、IIS等），
* 停止Adobe Campaign服务器： **网络停止nlserver6** 在Windows中， **/etc/init.d/nlserver6停止** 在Linux中，

  >[!NOTE]
  >
  >从20.1开始，我们建议改使用以下命令（对于Linux）： **systemctl stop nlserver**

* 在Linux中，使用 **ipcrm** 命令，
* 重新启动Adobe Campaign服务器： **网络启动nlserver6** 在Windows中， **/etc/init.d/nlserver6 start** 在Linux中，

  >[!NOTE]
  >
  >从20.1开始，我们建议改使用以下命令（对于Linux）： **systemctl启动nlserver**

* 重新启动Web服务器。

**示例**：考虑Linux下的配置。

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
>对于Linux，如果将 **webTrackingParamSize** 或 **maxSharedLogs** 参数，可能需要增加共享内存(SHM)的大小。
