---
product: campaign
title: 使用外部收件人表
description: 使用外部收件人表
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 16%

---

# 使用外部收件人表{#using-an-external-recipient-table}



如果投放表是外部表，则需要执行其他配置。 必须扩展&#x200B;**[!UICONTROL nms:seedmember]**&#x200B;架构。 向种子地址添加制表符以定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在这种情况下，要将种子地址添加到投放，请直接在匹配选项卡中输入适当的字段，或导入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

**nms：seedMember**&#x200B;架构扩展为[此节](../../configuration/using/seed-addresses.md)。
