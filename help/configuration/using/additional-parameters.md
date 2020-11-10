---
title: 其他Web跟踪参数
description: 进一步了解Web跟踪参数
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
translation-type: tm+mt
source-git-commit: 36fef519be93b33d55a96992c1ce234f2eaea696
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---


# 其他参数{#additional-parameters}

## 参数定义 {#definition-of-parameters}

您的Adobe Campaign平台将两个TRANSACTION类型的Web跟踪参数优惠为标准：

* **amount**:表示交易金额，
* **文章**:表示事务处理中的项数。

这些参数在nms:webTrackingLog **模式中定义** ，是报告中看到的一些指标。

要定义其他参数，必须扩展此模式。

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

您可以通过配置跟踪日志列表(投放或收件人)来显示这些参数的值。

## 重定向服务器配置 {#redirection-server-configuration}

在服务器配置中，您可以定义要考虑到Web跟踪参数的最大字符数。

>[!IMPORTANT]
>
>增加要考虑的最大字符数可能会影响平台的Web跟踪性能。

为此，请修 **改serverConf.xml文** 件中元素 **`<trackinglogd>`** 的webTrackingParamSize属性 **** 。 此文件保存在 **Adobe Campaign** 安装目录的conf子目录中。

**示例**:

默认值为64个字符。 此值允许您考虑 **amount****和** article(&quot;amount=xxxxxxxxx&amp;article=xxxxxxxxx&quot;)标准参数。

通过考虑上述扩展模式示例中指示的两个参数（名称大小+值大小），您可以修改配置以考虑100个字符(&quot;amount=xxxxxxxxxxxx&amp;article=xxxxxxxxx&amp;mode=xxxxxxxxxxxxx&amp;code=xxxxxx&quot;)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改配置后，您必须：

* 停止承载重定向模块（Apache、IIS等）的Web服务器，
* 停止Adobe Campaign服务器： **net stop nlserver6在Windows** 中，/etc/init.d **/nlserver6在Linux中停止** ,

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）: **systemctl停止nserver**

* 在Linux中，使用ipcrm命令删除共享 **内存** 段，
* 重新启动Adobe Campaign服务器： **网络开始Windows中的** nlserver6, **/etc/init.d/nlserver6在Linux中的开始** ,

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）: **systemctl开始nlserver**

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
>对于Linux，如果您增加 **webTrackingParamSize** 或 **** maxSharedLogs参数的大小，则可能需要增加共享内存(SHM)的大小。

