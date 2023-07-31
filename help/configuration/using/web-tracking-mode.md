---
product: campaign
title: Web 跟踪模式
description: 了解如何选择Web跟踪模式
feature: Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 1%

---

# Web 跟踪模式{#web-tracking-mode}



Adobe Campaign允许您选择Web跟踪模式，该模式定义在应用程序中处理跟踪日志的方式。

有三种可用的Web跟踪模式： **&quot;会话跟踪&quot;**，**&quot;永久跟踪&quot;** 和 **&quot;匿名跟踪&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每种模式都有其各自的特点。 “永久”Web跟踪模式包括“会话”Web跟踪模式的特征，“匿名”模式包括“永久”和“会话”模式的特征。

>[!IMPORTANT]
>
>如果启用了“潜在客户”包，则默认情况下会启用“匿名”Web跟踪模式。 在所有其他情况下，默认启用“会话”Web跟踪模式。
>
>可以随时在实例部署向导中更改默认模式。

请注意，如果您使用 **永久web** 或 **匿名** 模式，则必须将索引添加到跟踪表(trackingLogXXX)的“sourceID”列(uuid230)：

1. 确定与永久跟踪有关的跟踪表。
1. 通过添加以下行扩展与这些表匹配的架构：

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永久** 和 **匿名** Web跟踪模式包括两个选项： **强制投放** 和 **上次投放**.

此 **强制投放** 选项允许您在跟踪期间指定投放(@jobid)的标识符。

此 **上次投放** 选项允许您将当前跟踪日志链接到上次跟踪的投放。

**会话Web跟踪的特征：**

此模式会为拥有会话Cookie的用户创建跟踪日志。 这些用户在Adobe Campaign发送的电子邮件中单击了URL，因此允许我们跟踪以下信息：

* 投放 ID
* 联系人ID
* 投放日志
* 永久cookie (uuid230)
* 跟踪URL
* 跟踪日志的日期

在此Web跟踪模式下，如果缺少部分信息，则不会在应用程序中创建跟踪日志。

此模式在容量（trackingLog表中的记录数量有限）和计算（无协调）方面比较经济。

**永久Web跟踪模式的特征：**

通过此Web跟踪模式，可根据永久uuid230 Cookie的存在情况创建跟踪日志。 如果访客关闭其会话，Adobe Campaign会使用永久Cookie从以前的跟踪日志中恢复有关访客的信息。 如果当前会话的uuid230与跟踪表中已存储的uuid230具有相同的值，Adobe Campaign会重新插入跟踪日志。

这意味着之前需要在Adobe Campaign中识别访客（通过投放），以启用对uuid230值的协调。

默认情况下，以前的跟踪日志中的搜索在“trackingLog”表中执行。 如果Leads包已启用，则在搜索“trackingLog”表之前，Adobe Campaign将在“incomingLead”表中搜索以前的跟踪日志记录。

在日志协调期间，此模式在计算方面成本高昂。

**匿名Web跟踪模式的特征：**

通过此Web跟踪模式，可检索链接到Adobe Campaign中的匿名浏览的跟踪日志。 每次单击跟踪的URL，都会自动创建一个跟踪日志。 此日志的值为uuid230。 在营销活动期间，将自动创建包含所有标识信息的跟踪日志（请参阅会话跟踪）。 Adobe Campaign将自动在以前的日志中搜索等于此营销活动跟踪日志值的“uuid230”值。 如果发现相同的值，则会使用营销活动跟踪日志中的所有信息输入所有以前的跟踪日志。

这种模式在计算量和体积方面成本最高。

>[!NOTE]
>
>如果 **[!UICONTROL Leads]** 软件包已安装，您需要对活动表执行相同的操作(**crm：incomingLead**)

以下架构总结了所有三种Web跟踪模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**基于上次投放的永久Web跟踪示例：**

Florence会收到投放、打开电子邮件、单击链接、浏览零售网站但不进行任何购买。 第二天，佛罗伦萨回到零售网站，浏览并购物。 由于启用了永久网络跟踪（最后一次投放），她第二次访问的所有日志都将链接到前一天发送给她的投放。
