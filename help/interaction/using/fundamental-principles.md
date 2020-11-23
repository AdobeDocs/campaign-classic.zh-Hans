---
solution: Campaign Classic
product: campaign
title: 基本原则
description: 基本原则
audience: interaction
content-type: reference
topic-tags: general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---


# 基本原则{#fundamental-principles}

## 部署环境 {#deploying-environments}

管理环境时，每个定位维度使用两个优惠:

* 一种设计环境,优惠经理负责创建和分类优惠、编辑并启动审批流程，以便使用它们。 每个类别的规则、可向其展示优惠的优惠空间以及用于定义优惠资格的预定义过滤器也在此环境中定义。

   类别还可以在联机环境中手动发布。

   批准优惠的过程详见批准 [和激活优惠部分](../../interaction/using/approving-and-activating-an-offer.md) 。

* 在实时环境中，可以找到设计环境的已批准优惠以及设计环境中配置的各种优惠空间、过滤器、类别和规则。 在调用优惠引擎期间，引擎将始终使用实时环境中的优惠。

优惠仅部署在批准过程中选定的优惠空间上。 因此，优惠在同样活着的优惠空间上可以生存但无法使用。

![](assets/architecture_interaction1.png)

## 交互类型和联系方法 {#interaction-types-and-contact-methods}

交互有两种可能类型：入站交互（由联系人发起）和出站交互(由优惠制作者发起)。

这两种交互可以在单一模式下进行(为单个接触计算优惠)，也可以在批处理模式下进行(为一组接触计算优惠)。 一般来说，入站交互是以酉模式进行的，出站交互是以批处理模式进行的。 但是，对于事务性消息（例如，出站交互以统一模式进行），可能存在某些例 [外情况](../../message-center/using/about-transactional-messaging.md)。

只要能够或必须呈现优惠（根据所执行的配置）,优惠引擎就起到中介作用：它通过组合收到的关于联系人的数据和应用程序中指定的可以应用的不同规则，自动计算可用联系人之间的最佳可能优惠。

![](assets/architecture_interaction2.png)

