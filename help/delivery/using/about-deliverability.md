---
title: 关于Adobe Campaign Classic中的可交付性
description: 了解有关在Adobe Campaign Classic中管理可交付性的更多信息。
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# 关于投放能力{#about-deliverability}

Adobe Campaign提供了若干工具来跟踪平台的可交付性能。 本节还强调了管理和优化交付能力时应牢记的主要原则。

## 配置 {#configuration}

此功能可通过Adobe Campaign中的专用包获得。 要使用它，必须安装此包。 完成后，重新启动服务器以考虑要考虑的包。
* 对于托管和混合客户端， **Adobe技术支持和顾问在您的实例上配置了** “交付性”监控。 有关详细信息，请与您的Adobe客户经理联系。

* 对于内部部署安装，必须通过> **[!UICONTROL Deliverability monitoring (Email Deliverability)]** >菜单安装包 **[!UICONTROL Tools]****[!UICONTROL Advanced]****[!UICONTROL Import package]** 。 有关此方面的详细信息，请参 [阅安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。

在Adobe Campaign Classic中，可 **交付性监视** ，由工作流 **[!UICONTROL Refresh for deliverability]** 管理。 它默认安装在所有实例中，允许您初始化弹回邮件资格规则列表、域列表和MX列表。 安装包 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 后，此工作流会在夜间运行，以定期更新规则列表，并使您能够主动管理平台交付性。

## 背景 {#background}

电子邮件的发送能力对营销人员来说是一个重大挑战——无论他们发送几千条消息还是几十亿条消息。 每五条邮件中就有一条永远无法到达收件箱或其预期收件人。

一旦被归为IT部门的“技术问题”，电子邮件交付能力在营销日程上继续提升。 这是因为，精明的营销人员认识到，尽管其许多元素本质上都是技术性的，但可交付性最终还是一个业务问题，并且会带来重大的收入影响。

考虑电子邮件营销漏斗。 可交付性决定接收的消息数，这进而影响漏斗的每个后续阶段。 收到的电子邮件数量减少，导致打开次数减少、点击次数减少，转化率降低。 **对于拥有大型数据库的公司来说，平均和卓越的可交付性之间的差异实际上意味着几十万到几百万美元的收入。**

![](assets/deliverability_overview_1.png)

营销人员通过确定平均(80%)的可交付性，将大量转化率和美元留在谈判桌上。

电子邮件的可发送性到底是什么？ 营销人员如何提高投放率以扩大渠道的嘴巴，并从电子邮件营销活动中获得更多成效？

电子邮件发送能力是指一系列特征，这些特征决定了邮件在短时间内通过个人电子邮件地址到达其目的地的能力，以及在内容和格式方面达到预期质量的能力。 这些特征分为四大类：数据质量、消息和内容、发送基础架构和声誉。 它们共同构成了成功电子邮件交付计划的基础。 此概述概括介绍了电子邮件交付成功的四个基本要素，并提供了触及收件箱和从电子邮件营销计划中增加收入的最佳实践。

![](assets/deliverability_overview_2.png)
