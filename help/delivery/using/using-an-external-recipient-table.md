---
product: campaign
title: 使用外部收件人表
description: 使用外部收件人表
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# 使用外部收件人表{#using-an-external-recipient-table}

![](../../assets/common.svg)

如果投放表是外部表，则需要进行其他配置。 的 **[!UICONTROL nms:seedmember]** 必须扩展架构。 种子地址中会添加一个选项卡以定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在这种情况下，要向投放添加种子地址，请直接在匹配选项卡中输入足够的字段，或导入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

的 **nms:seedMember** 模式扩展 [此部分](../../configuration/using/seed-addresses.md).
