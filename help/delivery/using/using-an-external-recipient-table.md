---
product: campaign
title: 使用外部收件人表
description: 使用外部收件人表
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# 使用外部收件人表{#using-an-external-recipient-table}



如果投放表是外部表，则需要进行其他配置。 的 **[!UICONTROL nms:seedmember]** 必须扩展架构。 种子地址中会添加一个选项卡以定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在这种情况下，要向投放添加种子地址，请直接在匹配选项卡中输入足够的字段，或导入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

的 **nms:seedMember** 模式扩展 [此部分](../../configuration/using/seed-addresses.md).
