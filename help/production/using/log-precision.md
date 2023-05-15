---
product: campaign
title: 日志精度
description: 日志精度
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# 日志精度{#log-precision}



您可以将此过程应用于所有Adobe Campaign模块，以提高日志精度。

它涉及使用更高级别的日志重新启动流程。

>[!IMPORTANT]
>
>此过程会取消此模块中正在进行的服务。

Adobe Campaign可以使用两个级别的日志进行操作：

1. 的 **详细** 模式是标准级别之后的第一个级别。 以下命令将激活它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   检查错误是否实际发生，然后以正常方式重新启动该进程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. 的 **TraceFilter** 模式，用于保存最大量的日志。 它通过以下命令激活：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用 **跟踪过滤器：&#42;**，则激活所有日志类型：ncm， rdr， nms， jst，时间， wdbc， ldap， soap， xtk， xtkquery，会话， xtkwriter，网络， pop3, inmail\
   >最有用的日志类型包括： **wdbc** （显示所有SQL查询）， **肥皂** （显示所有SOAP调用）， **ldap** （验证后显示所有LDAP查询）， **xtkquery** （显示所有querydef的列表）。\
   >您可以单独使用它们(**tracefilter:soap，wdbc** 例如)。 您还可以全部激活它们，并选择排除某些其他组件： **-tracefilter:&#42;,!soap**

   检查错误是否实际发生，然后以正常方式重新启动该进程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>这些命令的日志存储在模块的日志文件中。

以下是特定于Web模块的示例。 其他模块按如上所述运行。

在发送此命令之前，请检查没有正在进行的作业会受到影响：

```
nlserver pdump -who
```

接下来，关闭并重新启动 **TraceFilter** 模式：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一个示例：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>的 **Tracefile** 模式可让您保存日志。 在以上示例中，日志保存在 **var/`<instance-name>`/mta_debug.log** 和 **var/default/web_debug.log** 文件。

>[!IMPORTANT]
>
>在Windows中，请勿添加LD_PRELOAD选项。 以下命令足以：\
>nlserver web -tomcat -verbose -tracefilter:&#42;

检查问题是否再次发生，然后重新启动模块：

```
nlserver restart web -tomcat -noconsole
```

文件中提供了所有信息 **/usr/local/neolane/nl6/var/default/log/web.log**.
