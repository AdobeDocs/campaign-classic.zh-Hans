---
product: campaign
title: 配置在线调查
description: 了解如何配置在线调查
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Surveys
exl-id: 387bc362-4064-4181-9385-8e0c3423ba3e
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 配置在线调查{#configuring-surveys}



## 调查属性 {#survey-properties}

在线调查是完全可配置和定制的，可满足您的要求。 必须在属性窗口中输入参数。

有关可用参数的详情，请参见 [本文档](../../web/using/defining-web-forms-properties.md).

![](assets/s_ncs_admin_survey_properties_general.png)

## 调查数据存储 {#survey-data-storage}

默认情况下，Web窗体字段存储在收件人表中。 要使用其他表，请在 **[!UICONTROL Document type]** 字段。 此 **[!UICONTROL Zoom]** 图标用于查看选定表的内容。

由用户提供的调查答案未存储在字段中（而是存储在本地变量中），这些答案将存储在 **调查答案** 表格。 您可以更改所使用的架构，这些架构基于 **[!UICONTROL Library]** 字段。 此字段仅可用于 **调查**.
