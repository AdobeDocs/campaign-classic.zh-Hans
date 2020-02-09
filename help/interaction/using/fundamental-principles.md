---
title: 基本原则
seo-title: 基本原则
description: 基本原则
seo-description: null
page-status-flag: never-activated
uuid: 1ed3982b-7f9f-494d-8603-e856859bc31a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 695cf33f-1cc7-4ae8-8ef6-05aa65219411
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 基本原则{#fundamental-principles}

## 部署环境 {#deploying-environments}

管理选件时使用的每个定位维有两个环境：

* 一个设计环境，其中选件管理者负责创建和分类选件、编辑选件以及启动审批流程，以便使用它们。 在此环境中还定义了每个类别的规则、可在其中显示选件的选件空间以及用于定义选件资格的预定义筛选器。

   还可以在联机环境中手动发布类别。

   批准优惠的过程在批准和激活 [优惠部分中有详细说明](../../interaction/using/approving-and-activating-an-offer.md) 。

* 可以在实时环境中找到设计环境中已批准的选件，以及设计环境中配置的各种选件空间、过滤器、类别和规则。 在调用选件引擎期间，引擎将始终使用实时环境中的选件。

选件仅部署在批准过程中选定的选件空间上。 因此，某个选件可能是实时的，但在同时是实时的选件空间上无法使用。

![](assets/architecture_interaction1.png)

## 交互类型和联系方法 {#interaction-types-and-contact-methods}

有两种可能的交互类型：入站交互（由联系人发起）和出站交互（由优惠制作者发起）。

这两种类型的交互可以在单一模式（为单个接触计算选件）或批处理模式（为一组接触计算选件）中执行。 一般而言，入站交互以单一模式进行，出站交互以批处理模式进行。 但是，对于例如交易消息，可能存在某些例外情况，由此，出站交互以统一模式进行(请参阅 [本节](../../message-center/using/about-transactional-messaging.md))。

一旦能够或必须展示某个选件（根据所执行的配置），该选件引擎就起到中介作用：它通过组合接收的关于联系人的数据和可以应用在应用程序中指定的不同规则，自动计算可用联系人的最佳可能出价。

![](assets/architecture_interaction2.png)

