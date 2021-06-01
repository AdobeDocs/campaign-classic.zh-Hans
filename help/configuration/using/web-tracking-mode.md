---
product: campaign
title: Web 跟踪模式
description: Web 跟踪模式
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---

# Web 跟踪模式{#web-tracking-mode}

Adobe Campaign允许您选择Web跟踪模式，该模式定义在应用程序中处理跟踪日志的方式。

有三种可用的Web跟踪模式：**&quot;会话跟踪&quot;**、**&quot;永久跟踪&quot;**&#x200B;和&#x200B;**&quot;匿名跟踪&quot;**。

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每种模式都有特定的特点。 “永久”Web跟踪模式包括“会话”Web跟踪模式的特征，而“匿名”模式包括“永久”和“会话”模式的特征。

>[!IMPORTANT]
>
>如果启用了“潜在客户”包，则默认情况下会启用“匿名”Web跟踪模式。 在所有其他情况下，默认启用“会话”Web跟踪模式。
>
>可以随时在实例部署向导中更改默认模式。

请注意，如果您使用&#x200B;**perment web**&#x200B;或&#x200B;**anonymous**&#x200B;跟踪模式，则必须在跟踪表(trackingLogXXX)的“sourceID”列(uuid230)中添加一个索引：

1. 确定与永久跟踪相关的跟踪表。
1. 通过添加以下行来扩展与这些表匹配的架构：

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**** 永久和匿 **** 名Web跟踪模式包括两个选项： **强制** 投放和 **上次投放**。

使用&#x200B;**强制投放**&#x200B;选项，可在跟踪期间指定投放的标识符(@jobid)。

**上次投放**&#x200B;选项允许您将当前跟踪日志链接到上次跟踪的投放。

**会话Web跟踪的特点：**

此模式会为具有会话Cookie的用户创建跟踪日志。 这些用户点击了Adobe Campaign发送的电子邮件中的URL，以便我们能够跟踪以下信息：

* 投放ID
* 联系人ID
* 投放日志
* 永久cookie(uuid230)
* 跟踪URL
* 跟踪日志的日期

在此Web跟踪模式下，如果缺少部分信息，则不会在应用程序中创建跟踪日志。

此模式在卷数（trackingLog表中记录的有限数量）和计算（无协调）方面非常经济。

**永久Web跟踪模式的特点：**

通过此Web跟踪模式，您可以基于永久uid230 Cookie的存在创建跟踪日志。 如果访客关闭其会话，Adobe Campaign会使用永久Cookie从以前的跟踪日志中恢复与其相关的信息。 如果当前会话的uuid230与跟踪表中已存储的uuid230具有相同的值，则Adobe Campaign会重新插入跟踪日志。

这意味着之前需要在Adobe Campaign中（通过投放）识别访客，才能对uuid230值进行协调。

默认情况下，会在“trackingLog”表中执行先前跟踪日志中的搜索。 如果启用了潜在客户包，则在搜索“trackingLog”表之前，Adobe Campaign将搜索“incomingLead”表以查找以前的跟踪日志记录。

在日志协调期间，此模式的计算成本很高。

**匿名Web跟踪模式的特点：**

此Web跟踪模式允许您检索链接到Adobe Campaign中匿名浏览的跟踪日志。 每次点击跟踪的URL时，会自动创建跟踪日志。 此日志的值仅为uuid230。 在营销活动期间，会自动创建一个包含所有标识信息的跟踪日志（请参阅会话跟踪）。 Adobe Campaign将自动在以前的日志中搜索与此营销活动的跟踪日志中的值相等的“uuid230”值。 如果找到相同的值，则会输入所有以前的跟踪日志以及营销活动跟踪日志中的所有信息。

在计算和数量方面，此模式成本最高。

>[!NOTE]
>
>如果安装了&#x200B;**[!UICONTROL Leads]**&#x200B;包，则需要对活动表(**crm:incomingLead**)执行相同的操作

以下模式总结了所有三种Web跟踪模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**基于上次投放的永久Web跟踪示例：**

Florence收到投放，打开电子邮件，点击链接，浏览零售网站，但不进行任何购买。 第二天，佛罗伦萨回到零售网站，浏览并购买商品。 由于启用了永久性Web跟踪（上次投放），因此她第二次访问的所有日志都将链接到前一天发送给她的投放。
