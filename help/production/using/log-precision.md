---
product: campaign
title: 日志精度
description: 日志精度
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 2%

---

# 日志精度{#log-precision}



您可以将此流程应用于所有Adobe Campaign模块，以提高日志精度。

它涉及使用更高级别的日志来重新启动流程。

>[!IMPORTANT]
>
>此过程将取消此模块中正在进行的服务。

Adobe Campaign可以使用两个级别的日志进行操作：

1. 此 **详细** 模式是标准级别之后的第一个级别。 以下命令将激活它：

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   检查是否确实发生了错误，然后以正常方式重新启动该过程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. 此 **TraceFilter** 模式，可让您保存最多的日志。 它可通过以下命令激活：

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >如果您使用 **tracefilter：&#42;**，所有日志类型均已激活：ncm、rdr、nms、jst、timing、wdbc、ldap、soap、xtk、xtkquery、session、xtkwriter、network、pop3、inmail\
   最有用的日志类型包括： **wdbc** （显示所有SQL查询）、 **soap** （显示所有SOAP调用）， **ldap** （在验证后显示所有LDAP查询）， **xtkquery** （显示所有querydef列表）。\
   您可以单独使用它们(**tracefilter：soap，wdbc** 例如)。 您还可以全部激活它们，然后选择排除某些其他节点： **-tracefilter：&#42;，！soap**

   检查是否确实发生了错误，然后以正常方式重新启动该过程：

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
这些命令的日志存储在模块的日志文件中。

以下是特定于Web模块的示例。 其它模块按上述方式运行。

在发送此命令之前，请检查任何正在进行的作业都不会受到影响：

```
nlserver pdump -who
```

接下来，关闭并重新启动模块 **TraceFilter** 模式：

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

另一个例子：

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
此 **追踪文件** 模式允许您保存日志。 在上面的示例中，日志保存在 **var/`<instance-name>`/mta_debug.log** 和 **var/default/web_debug.log** 文件。

>[!IMPORTANT]
>
在Windows中，不要添加LD_PRELOAD选项。 以下命令就足够了：\
nlserver web -tomcat -verbose -tracefilter：&#42;

检查问题是否再次出现，然后重新启动模块：

```
nlserver restart web -tomcat -noconsole
```

所有信息都可在文件中找到 **/usr/local/neolane/nl6/var/default/log/web.log**.
