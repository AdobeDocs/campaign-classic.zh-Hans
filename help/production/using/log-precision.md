---
solution: Campaign Classic
product: campaign
title: 日志精度
description: 日志精度
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---


# 日志精度{#log-precision}

您可以将此过程应用于所有Adobe Campaign模块，以提高日志精度。

它涉及使用更高级别的日志重新启动进程。

>[!IMPORTANT]
>
>此过程取消本模块中正在进行的服务。

Adobe Campaign可以使用两个级别的日志：

1. **Verbose**&#x200B;模式是标准级别之后的第一个级别。 以下命令激活它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   检查是否确实发生了错误，然后以正常方式重新启动进程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. **TraceFilter**&#x200B;模式，用于保存最多的日志。 它通过以下命令激活：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果使用&#x200B;**tracefilter:***，则激活所有日志类型：ncm， rdr， nms， jst，计时， wdbc， ldap， soap， xtk， xtkquery， session， xtkwriter， network， pop3, inmail\
   >最有用的日志类型有：**wdbc**(显示所有SQL查询)、**soap**（显示所有SOAP调用）、****(显示身份验证后的所有LDAP查询)、**xtkquery**(显示所有查询的列表)。\
   >可以单独使用它们（例如&#x200B;**tracefilter:soap，wdbc**）。 您还可以全部激活它们，并选择排除某些其他项：**tracefilter:*,!soap**

   检查是否确实发生了错误，然后以正常方式重新启动进程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>这些命令的日志存储在模块的日志文件中。

下面是一个特定于Web模块的示例。 其他模块如上所述操作。

在发送此命令之前，请检查是否不会影响正在进行的作业：

```
nlserver pdump -who
```

接下来，在&#x200B;**TraceFilter**&#x200B;模式下关闭并重新启动模块：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一个示例：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>使用&#x200B;**Tracefile**&#x200B;模式可以保存日志。 在以上示例中，日志保存在&#x200B;**var/`<instance-name>`/mta_debug.log**&#x200B;和&#x200B;**var/default/web_debug.log**&#x200B;文件中。

>[!IMPORTANT]
>
>在Windows中，请勿添加LD_PRELOAD选项。 以下命令就足够了：\
>nlserver web -tomcat -verbose -tracefilter:*

检查是否再次出现问题，然后重新启动模块：

```
nlserver restart web -tomcat -noconsole
```

文件&#x200B;**/usr/local/neolane/nl6/var/default/log/web.log**&#x200B;中提供所有信息。
