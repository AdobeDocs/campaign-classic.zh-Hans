---
solution: Campaign Classic
product: campaign
title: 其他Web跟踪参数
description: 进一步了解Web跟踪参数
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---


# 其他参数{#additional-parameters}

## 参数{#definition-of-parameters}的定义

您的Adobe Campaign平台将两个TRANSACTION类型的Web跟踪参数优惠为标准：

* **amount**:表示交易金额，
* **文章**:表示事务处理中的项数。

这些参数在&#x200B;**nms:webTrackingLog**&#x200B;模式中定义，是报告中看到的一些指示符。

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

## 重定向服务器配置{#redirection-server-configuration}

在服务器配置中，您可以定义要考虑到Web跟踪参数的最大字符数。

>[!IMPORTANT]
>
>增加要考虑的最大字符数可能会影响平台的Web跟踪性能。

为此，请修改&#x200B;**serverConf.xml**&#x200B;文件中&#x200B;**`<trackinglogd>`**&#x200B;元素的&#x200B;**webTrackingParamSize**&#x200B;属性。 此文件保存在Adobe Campaign安装目录的&#x200B;**conf**&#x200B;子目录中。

**示例**:

默认值为64个字符。 此值允许您考虑&#x200B;**amount**&#x200B;和&#x200B;**article**(&quot;amount=xxxxxxxxxxxx&amp;article=xxxxxxxx&quot;)标准参数。

通过考虑上述扩展模式示例中指示的两个参数（名称大小+值大小），您可以修改配置以考虑100个字符(&quot;amount=xxxxxxxxxxxx&amp;article=xxxxxxxxx&amp;mode=xxxxxxxxxxxxx&amp;code=xxxxxx&quot;)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改配置后，您必须：

* 停止承载重定向模块（Apache、IIS等）的Web服务器，
* 停止Adobe Campaign服务器：**net stop nlserver6**（在Windows中）,**/etc/init.d/nlserver6 stop**（在Linux中）,

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）:**systemctl停止nlserver**

* 在Linux中，使用&#x200B;**ipcrm**&#x200B;命令删除共享内存段，
* 重新启动Adobe Campaign服务器：**net开始nlserver6**（在Windows中）,**/etc/init.d/nlserver6开始**（在Linux中）,

   >[!NOTE]
   >
   >从20.1开始，我们建议改用以下命令（对于Linux）:**systemctl开始nlserver**

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

