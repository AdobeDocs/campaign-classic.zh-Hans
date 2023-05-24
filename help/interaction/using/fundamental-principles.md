---
product: campaign
title: 基本原则
description: 基本原则
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# 基本原则{#fundamental-principles}



## 部署环境 {#deploying-environments}

在管理选件时，使用的每个定向维度都有两个环境：

* 优惠经理负责创建和分类优惠、编辑优惠以及启动审批流程以便使用这些优惠的设计环境。 此环境中还定义了每个类别的规则、可在其中显示优惠的优惠空间以及用于定义优惠资格的预定义过滤器。

   类别也可以在在线环境中手动发布。

   有关优惠批准流程的详情，请参见 [批准和激活优惠](../../interaction/using/approving-and-activating-an-offer.md) 部分。

* 可以在实时环境中找到设计环境中的已批准选件，以及在设计环境中配置的各种选件空间、过滤器、类别和规则。 在调用优惠引擎期间，引擎将始终使用实时环境中的优惠。

仅在批准流程期间选定的优惠空间上部署优惠。 因此，选件可能是实时的，但在也是实时的选件空间上不可用。

![](assets/architecture_interaction1.png)

## 交互类型和联系方式 {#interaction-types-and-contact-methods}

交互有两种类型：入站交互（由联系人启动）和出站交互（由选件设计者启动）。

这两种类型的交互可以在单一模式（为单个联系人计算选件）或批量模式（为一组联系人计算选件）中执行。 通常，入站交互以单一模式执行，出站交互以批量模式执行。 但是，对于事务型消息，可能会存在一些例外，例如，出站交互以单一模式执行(请参阅 [本节](../../message-center/using/about-transactional-messaging.md))。

一旦可以或必须提供选件（根据执行的配置），选件引擎就会扮演中介角色：它通过组合接收到的有关联系人的数据和可在应用程序中应用的不同规则，自动计算可用联系人中可能的最佳选件。

![](assets/architecture_interaction2.png)
