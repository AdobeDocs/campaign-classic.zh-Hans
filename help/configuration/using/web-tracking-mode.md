---
title: Web 跟踪模式
seo-title: Web 跟踪模式
description: Web 跟踪模式
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 1%

---


# Web 跟踪模式{#web-tracking-mode}

Adobe Campaign允许您选择Web跟踪模式，该模式定义了在应用程序中处理跟踪日志的方式。

有三种可用的Web 跟踪模式： **“会话跟踪**”**、“永久跟踪** ”和“ **匿名跟踪”**。

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每种模式都有特定特征。 “永久”Web 跟踪模式包括“会话”Web 跟踪模式的特征，而“匿名”模式包括“永久”和“会话”模式的特征。

>[!IMPORTANT]
>
>如果启用“Lead”包，则默认情况下将启用“匿名”Web 跟踪模式。 在所有其他情况下，默认情况下启用“会话”Web 跟踪模式。
>
>可以随时在实例部署向导中更改默认模式。

请注意，如果您使 **用永久** Web **或匿名跟踪模式** ，则必须在跟踪表(trackingLogXXX)中的“sourceID”列(uuid230)中添加一个索引：

1. 确定与永久跟踪相关的跟踪表。
1. 通过添加以下行，扩展与这些表匹配的模式:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永久** 和匿 **名Web 跟踪** 模式包括两个选项： **强制投放** , **最后投放**。

强 **制投放** 选项允许您在跟踪过程中指定投放(@jobid)的标识符。

使用 **“上次投放** ”选项，您可以将当前跟踪日志链接到上次跟踪投放。

**会话Web 跟踪的特点：**

此模式为具有会话cookie的用户创建跟踪日志。 这些人点击了Adobe Campaign发送的电子邮件中的URL，因此可以跟踪以下信息：

* 投放ID
* 联系人ID
* 投放日志
* 永久cookie(uuid230)
* 跟踪URL
* 跟踪日志的日期

在此Web 跟踪模式下，如果缺少部分信息，则不会在应用程序中创建跟踪日志。

此模式在卷（trackingLog表中记录的有限数量）和计算（无协调）方面是经济的。

**永久Web 跟踪模式的特点：**

通过此Web 跟踪模式，您可以基于存在永久uuid230 cookie来创建跟踪日志。 如果访客关闭其会话，Adobe Campaign将使用永久cookie从以前的跟踪日志恢复有关其的信息。 Adobe Campaign如果当前会话的uuid230与跟踪表中已存储的uuid230具有相同的值，则重新插入跟踪日志。

这意味着，访客需要先前以Adobe Campaign(通过投放)进行标识，以启用uuid230值的协调。

默认情况下，在“trackingLog”表中执行以前跟踪日志中的搜索。 如果Leads包已启用，则在搜索“trackingLog”表之前，Adobe Campaign将搜索“incomingLead”表以查找以前的跟踪日志记录。

在日志协调期间，此模式的计算成本很高。

**匿名Web 跟踪模式的特点：**

此Web 跟踪模式允许您检索链接到Adobe Campaign中匿名浏览的跟踪日志。 每次单击跟踪的URL时，都会自动创建跟踪日志。 此日志仅具有uuid230的值。 在营销活动，系统会自动创建包含所有标识信息的跟踪日志（请参阅会话跟踪）。 Adobe Campaign将自动搜索以前日志中“uuid230”值，该值等于此营销活动的跟踪日志中的值。 如果找到相同的值，则输入所有以前的跟踪日志以及营销活动跟踪日志中的所有信息。

在计算和量方面，此模式成本最高。

>[!NOTE]
>
>如果安 **[!UICONTROL Leads]** 装了该包，则需要对活动表(crm:incomingLead **)执行相同操作**。

以下模式总结了所有三种Web 跟踪模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**基于上次投放的永久Web跟踪示例：**

佛罗伦萨收到投放，打开电子邮件，单击链接，浏览零售网站，但不进行任何购买。 第二天，佛罗伦萨回到零售网站，浏览并购买。 由于启用了永久Web跟踪(上次投放)，因此她第二次访问的所有日志都将链接到前一天发送给她的投放。
