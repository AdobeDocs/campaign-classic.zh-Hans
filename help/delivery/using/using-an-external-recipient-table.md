---
product: campaign
title: 使用外部收件人表
description: 使用外部收件人表
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
TQID: https://experienceleague.adobe.com/Uq5yqNYkyDrFVtueUlkIOEC9XEUaYtBArNy8-t1rKAw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 18%
---
# 使用外部收件人表{#using-an-external-recipient-table}



如果投放表是外部表，则需要执行其他配置。 必须扩展&#x200B;**[!UICONTROL nms:seedmember]**&#x200B;架构。 向种子地址添加制表符以定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在这种情况下，要将种子地址添加到投放，请直接在匹配选项卡中输入适当的字段，或导入地址模板：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

**nms:seedMember**&#x200B;架构扩展为[此节](../../configuration/using/seed-addresses.md)。
