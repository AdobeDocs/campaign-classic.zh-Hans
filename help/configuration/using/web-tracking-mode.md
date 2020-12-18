---
solution: Campaign Classic
product: campaign
title: Web 跟踪模式
description: Web 跟踪模式
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---


# Web 跟踪模式{#web-tracking-mode}

Adobe Campaign允许您选择Web跟踪模式，该模式定义了在应用程序中处理跟踪日志的方式。

有三种可用的Web 跟踪模式：**&quot;会话跟踪&quot;**,**&quot;永久跟踪&quot;**&#x200B;和&#x200B;**&quot;匿名跟踪&quot;**。

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每种模式都有特定特征。 “永久”Web 跟踪模式包括“会话”Web 跟踪模式的特征，而“匿名”模式包括“永久”和“会话”模式的特征。

>[!IMPORTANT]
>
>如果启用“Lead”包，则默认情况下将启用“匿名”Web 跟踪模式。 在所有其他情况下，默认情况下启用“会话”Web 跟踪模式。
>
>可以随时在实例部署向导中更改默认模式。

请注意，如果您使用&#x200B;**永久Web**&#x200B;或&#x200B;**匿名**&#x200B;跟踪模式，则必须在跟踪表(trackingLogXXX)中的“sourceID”列(uuid230)中添加索引：

1. 确定与永久跟踪相关的跟踪表。
1. 通过添加以下行，扩展与这些表匹配的模式:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永** 久和匿 **** 名网络跟踪模式包括两个选项： **强制** 送货 **和最后投放**。

使用&#x200B;**强制投放**&#x200B;选项，可以在跟踪期间指定投放的标识符(@jobid)。

使用&#x200B;**上一个投放**&#x200B;选项可以将当前跟踪日志链接到上一个跟踪投放。

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
>如果&#x200B;**[!UICONTROL Leads]**&#x200B;包已安装，则需要对活动表(**crm:incomingLead**)执行相同的操作

以下模式总结了所有三种Web 跟踪模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**基于上次投放的永久Web跟踪示例：**

佛罗伦萨收到投放，打开电子邮件，单击链接，浏览零售网站，但不进行任何购买。 第二天，佛罗伦萨回到零售网站，浏览并购买。 由于启用了永久Web跟踪(上次投放)，因此她第二次访问的所有日志都将链接到前一天发送给她的投放。
