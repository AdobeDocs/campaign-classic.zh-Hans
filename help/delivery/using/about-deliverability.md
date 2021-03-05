---
solution: Campaign Classic
product: campaign
title: 关于活动中的可交付性
description: 了解交付能力最佳实践
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 关于投放能力{#about-deliverability}

**Deliverability** 包括衡量您的活动在到达收件人收件箱时是否成功而不会弹跳或标记为垃圾邮件。

Adobe Campaign优惠了特定数量的工具来跟踪平台的可交付性能。 本节还强调了在管理和优化交付能力时应牢记的主要原则。

## 配置{#configuration}

此功能可通过Adobe Campaign中的专用包获得。 要使用它，必须安装此包。 完成后，重新启动服务器以便将包考虑在内。
* 对于托管和混合客户端，通过Adobe技术支持和顾问在您的实例上配置&#x200B;**可交付性监视**。 有关详细信息，请与Adobe客户经理联系。

* 对于内部部署安装，必须通过&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;菜单安装&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;包。 有关详细信息，请参阅[安装活动内置软件包](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign中，**可交付性监视**&#x200B;由&#x200B;**[!UICONTROL Refresh for deliverability]**&#x200B;工作流管理。 它默认安装在所有实例中，允许您初始化弹回邮件资格规则的列表、域的列表和MX的列表。 安装&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;包后，此工作流将在夜间运行，以定期更新规则的列表，并使您能够主动管理平台交付性。

## 背景{#background}

无论营销人员是发送几千条消息还是发送数十亿条消息，电子邮件的发送能力对营销人员来说都是一个重大挑战。 每五条邮件中就有一条永远无法到达收件箱或其预期收件人。

一旦被归为IT部门的“技术问题”，电子邮件交付能力将继续在营销议程上占据更高的位置。 这是因为，精明的营销人员认识到，尽管其许多元素本质上都是技术性的，但交付性最终还是一个业务问题，会对收入产生重大影响。

考虑电子邮件营销漏斗。 可交付性决定接收的消息数，这进而影响漏斗的每个后续阶段。 收到的电子邮件数量减少，结果将打开次数减少，点击次数减少，转化率减少。 **对于拥有大型数据库的公司来说，平均数据和高交付能力之间的差异实际上意味着几十万到百万美元的收入。**

![](assets/deliverability_overview_1.png)

通过满足平均(80%)的可交付性，营销人员将大量转化率和美元留在谈判桌前。

电子邮件的发送能力到底是什么？ 营销人员如何提高投放率，以扩大渠道并从电子邮件活动中榨取更多成果？

电子邮件可发送性是指一系列特征，这些特征决定了邮件在短时间内通过个人电子邮件地址到达其目的地的能力，并且在内容和格式方面具有预期的质量。 这些特征分为四个主要类别:数据质量、消息和内容、发送基础架构和声誉。 它们共同构成了成功的电子邮件交付项目的基础。 此概述概括介绍了电子邮件营销成功的四个基本要素，以及触及收件箱并从电子邮件营销项目中增加收入的优惠最佳实践。

<!--![](assets/deliverability_overview_2.png)-->
