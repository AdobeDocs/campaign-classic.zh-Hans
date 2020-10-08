---
title: 关于Adobe Campaign Classic的可交付性
description: 了解有关在Adobe Campaign Classic管理可交付性的更多信息。
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---


# 关于投放能力{#about-deliverability}

**交付性** ，包括衡量活动在到达收件人收件箱时是否成功，不会出现弹跳或标记为垃圾邮件。

Adobe Campaign优惠一定数量的工具来跟踪平台的可交付性能。 本节还重点介绍在管理和优化交付能力时应牢记的主要原则。

## 配置{#configuration}

此功能可通过Adobe Campaign专用包获得。 要使用它，必须安装此包。 完成后，重新启动服务器以便考虑包。
* 对于托管和混合客户端， **Adobe技术支持** 和顾问会在您的实例上配置可交付性监控。 有关详细信息，请与Adobe客户经理联系。

* 对于内部部署安装，必须通过> > **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 菜单安装 **[!UICONTROL Tools]** 包 **[!UICONTROL Advanced]****[!UICONTROL Import package]** 。 有关此方面的详细信息，请参 [阅安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign Classic, **可交付性监控** 由工作流进行 **[!UICONTROL Refresh for deliverability]** 管理。 它默认安装在所有实例中，并允许您初始化弹回邮件资格规则的列表、域的列表和MX的列表。 安装包 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 后，此工作流会在夜间运行，以定期更新规则的列表，并使您能够主动管理平台交付性。

## 背景 {#background}

无论营销人员是发送几千条邮件还是发送几十亿条邮件，电子邮件的发送能力对营销人员来说都是一个重大挑战。 每五条邮件中就有一条永远无法到达收件箱或其预期收件人。

一旦被归为IT部门的“技术问题”，电子邮件交付能力在营销议程上的地位将继续提高。 这是因为，精明的营销人员认识到，尽管其许多要素在性质上都是技术性的，但可交付性最终还是一个业务问题，并且会产生重大的收入影响。

考虑电子邮件营销漏斗。 可交付性决定接收的消息数，这进而影响漏斗的每个后续阶段。 打开次数、点击次数和转化率都会减少收到的电子邮件数量。 **对于拥有大型数据库的公司来说，平均数据和卓越数据交付能力之间的差异，可能意味着几十万到几百万美元的收入。**

![](assets/deliverability_overview_1.png)

营销人员通过平均(80%)的可交付性达成共识，将大量转化率和美元留在谈判桌前。

电子邮件的发送能力究竟是什么？ 营销人员如何提高投放率以扩大漏斗的嘴巴并从电子邮件活动中榨取更多结果？

电子邮件发送能力是指一组特征，这些特征决定了邮件在短时间内通过个人电子邮件地址到达其目的地的能力，并且在内容和格式方面具有预期的质量。 这些特征分为四个主要类别:数据质量、消息和内容、发送基础架构和声誉。 它们共同构成了成功电子邮件交付项目的基础。 本概述概括介绍了成功发送电子邮件的四个基本要素，以及优惠触及收件箱和从电子邮件营销项目增加收入的最佳实践。

<!--![](assets/deliverability_overview_2.png)-->
