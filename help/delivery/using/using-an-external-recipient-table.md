---
product: campaign
title: 使用外部收件人表
description: 使用外部收件人表
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 16%

---

# 使用外部收件人表{#using-an-external-recipient-table}



如果投放表是外部表，则需要执行其他配置。 此 **[!UICONTROL nms:seedmember]** 必须扩展架构。 向种子地址添加制表符以定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在这种情况下，要将种子地址添加到投放，请直接在匹配选项卡中输入适当的字段，或导入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

此 **nms：seedMember** 模式扩展为 [本节](../../configuration/using/seed-addresses.md).
