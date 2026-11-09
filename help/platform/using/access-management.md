---
product: campaign
title: 权限快速入门
description: 了解如何授予对Campaign功能的访问权限
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
TQID: 'https://experienceleague.adobe.com/03hVUeg0dRIFz0J20RfxH4EdSmAhe9h2c9BfKB-qJUs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
    internal-label: Permissions
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: 0fdce84d7da1ff42a406ace8f1a180f6a426646a
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 9%
---
# 权限快速入门{#access-management}

Adobe Campaign 允许您定义和管理分配给各种操作员的权限。 这些权限是一组授权或拒绝的权限和限制：

* 访问特定功能（通过指明权限），
* 访问特定记录，
* 创建、修改和/或删除记录（操作、联系人、营销活动、组等）。

>[!NOTE]
>
>作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关权限以及如何定义文件夹权限的更多信息，请参阅Campaign v8文档：
>
>* [开始使用权限](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}
>* [添加文件夹权限](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/folder-permissions){target="_blank"}
>
>[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}

## 身份验证模式 {#authentication-mode}

>[!CAUTION]
>
>从Campaign Classic v7.3.1开始，所有操作员都应使用[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}连接到Campaign。
>
>在Campaign v7中，仍可以使用登录/密码进行本机身份验证。 但是，为了增强安全性和身份验证过程，Adobe Campaign强烈建议您将所有现有操作员从本机身份验证迁移到Adobe IMS。 请注意，在Campaign v8中，不允许使用本机身份验证连接。

* 要迁移操作员，请参阅[将用户迁移到IMS](../../technotes/using/migrate-users-to-ims.md)。
* 若要迁移最终用户的身份验证模式，请参阅[迁移最终用户身份验证模式](../../technotes/using/ac-ims.md)。

此迁移后，权限通过Adobe IMS进行管理。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}以了解如何设置它们。


<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/manage-permissions){target="_blank"} (Campaign v8 documentation).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/manage-permissions){target="_blank"} (Campaign v8 documentation)

* [Manage Campaign folder access](access-management.md)

* [Access rights matrix](assets/access-rights-matrix.pdf)


See also:

* [Manage permissions for workflows](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/advanced-management/managing-rights){target="_blank"} (Campaign v8 documentation)
* [Manage permissions for distributed marketing](https://experienceleague.adobe.com/en/docs/campaign/automation/distributed-marketing/about-distributed-marketing#operators-and-entities){target="_blank"} (Campaign v8 documentation)
* [Manage permissions for the interaction module](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/offers/interaction-settings/interaction-operators){target="_blank"} (Campaign v8 documentation)
* [Filter access to schemas](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/filter-schema){target="_blank"} (Campaign v8 documentation)
* [Restricting PI view](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/restrict-pi-view){target="_blank"} (Campaign v8 documentation)
-->