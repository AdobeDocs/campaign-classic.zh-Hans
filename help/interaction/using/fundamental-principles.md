---
product: campaign
title: 基本原则
description: 基本原则
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# 基本原则{#fundamental-principles}



## 部署环境 {#deploying-environments}

在管理选件时，所使用的每个定向维度都有两个环境：

* 一种设计环境，在此环境中，优惠经理负责创建和分类优惠、编辑优惠以及启动审批流程，以便使用这些优惠。 此环境中还定义了每个类别的规则、可在其中显示优惠的优惠空间，以及用于定义优惠资格的预定义过滤器。

  类别也可以在在线环境中手动发布。

  有关批准优惠的详细流程，请参见 [批准和激活优惠](../../interaction/using/approving-and-activating-an-offer.md) 部分。

* 可以在实时环境中找到设计环境中的已批准选件，以及在设计环境中配置的各种选件空间、过滤器、类别和规则。 在调用选件引擎期间，引擎将始终使用实时环境中的选件。

选件仅部署在批准流程期间选择的选件空间上。 因此，选件可能是实时的，但无法用于同时处于实时状态的选件空间。

![](assets/architecture_interaction1.png)

## 交互类型和联系方法 {#interaction-types-and-contact-methods}

交互有两种类型：入站交互（由联系人启动）和出站交互（由选件设计者启动）。

这两种类型的交互可以在单一模式（为单个联系人计算选件）或批量模式（为一组联系人计算选件）中执行。 通常，入站交互以单一模式执行，出站交互以批处理模式执行。 然而，对于事务型消息来说，可能会存在一些例外，例如出站交互以单一模式执行(请参阅 [本节](../../message-center/using/about-transactional-messaging.md))。

一旦能够或必须提供选件（根据执行的配置），选件引擎就会起到中介作用：它通过组合接收到的有关联系人的数据和可在应用程序中应用的不同规则，自动计算可用联系人中可能的最佳选件。

![](assets/architecture_interaction2.png)
