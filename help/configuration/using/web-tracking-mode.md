---
title: Web跟踪模式
seo-title: Web跟踪模式
description: Web跟踪模式
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Web跟踪模式{#web-tracking-mode}

Adobe Campaign允许您选择Web跟踪模式，该模式定义在应用程序中处理跟踪日志的方式。

有三种可用的Web跟踪模式：“ **会话跟踪”**、**“永久跟踪”** 和“ **匿名跟踪”**。

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每种模式都有特定的特性。 “永久”Web跟踪模式包括“会话”Web跟踪模式的特性，而“匿名”模式包括“永久”和“会话”模式的特性。

>[!IMPORTANT]
>
>如果启用“Lead”包，则默认情况下将启用“匿名”Web跟踪模式。 在所有其他情况下，默认情况下启用“会话”Web跟踪模式。
>
>可以随时在实例部署向导中更改默认模式。

请注意，如果您使用的是 **永久Web** 或匿名跟踪模式 **** ，则必须在跟踪表(trackingLogXXX)中的“sourceID”列(uuid230)中添加一个索引：

1. 确定与永久跟踪相关的跟踪表。
1. 通过添加以下行来扩展与这些表匹配的架构：

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永久****和匿名** Web跟踪模式包括两个选项：强制 **交付****和上次交付**。

“强 **制交付** ”选项允许您在跟踪期间指定交付的标识符(@jobid)。

使用 **上次传送** ，您可以将当前跟踪日志链接到上次跟踪的传送。

**会话Web跟踪的特性：**

此模式为具有会话Cookie的用户创建跟踪日志。 这些人点击了Adobe Campaign发送的电子邮件中的URL，因此我们可以跟踪以下信息：

* 交付ID
* 联系人ID
* 交付日志
* 永久Cookie(uuid230)
* 跟踪URL
* 跟踪日志的日期

使用此Web跟踪模式时，如果缺少部分信息，则不会在应用程序中创建跟踪日志。

此模式在卷（trackingLog表中记录的有限数量）和计算（无调节）方面是经济的。

**永久Web跟踪模式的特点：**

通过此Web跟踪模式，您可以基于存在永久uuid230 cookie来创建跟踪日志。 如果访客关闭其会话，Adobe Campaign会使用永久cookie从以前的跟踪日志中恢复与他们相关的信息。 如果当前会话的uuid230与已存储在跟踪表中的uuid230具有相同的值，则Adobe Campaign会重新插入跟踪日志。

这意味着访客需要先前在Adobe Campaign中识别（通过交付），才能启用uuid230值的对帐。

默认情况下，在“trackingLog”表中执行先前跟踪日志中的搜索。 如果Lead包已启用，则在搜索“trackingLog”表之前，Adobe Campaign将搜索“incomingLead”表以查找以前的跟踪日志记录。

在日志协调期间，此模式的计算成本很高。

**匿名Web跟踪模式的特点：**

通过此Web跟踪模式，您可以检索链接到Adobe Campaign中匿名浏览的跟踪日志。 系统会为每次单击跟踪的URL自动创建跟踪日志。 此日志仅具有uuid230的值。 在营销活动过程中，会自动创建一个包含所有标识信息的跟踪日志（请参阅会话跟踪）。 Adobe Campaign将自动搜索以前的日志，以查找与此营销活动的跟踪日志中的值相等的“uuid230”值。 如果找到相同的值，则会输入所有以前的跟踪日志以及营销活动跟踪日志中的所有信息。

在计算和量方面，此模式成本最高。

>[!NOTE]
>
>如果安 **[!UICONTROL Leads]** 装了该包，您需要对活动表(**crm:incomingLead**)执行相同的操作

以下架构总结了所有三种Web跟踪模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**基于上次交付的永久Web跟踪示例：**

Florence收到一个递送，打开电子邮件，单击链接，浏览零售网站，但不进行任何购买。 第二天，佛罗伦萨回到零售网站，浏览并购买。 由于启用了永久Web跟踪（上次发送），她第二次访问的所有日志都将链接到前一天发送给她的发送。
