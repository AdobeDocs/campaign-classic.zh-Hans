---
product: campaign
title: 技术说明 — Adobe Campaign系统升级
description: Adobe Campaign系统升级
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: bffad77458ab0b4d40490a52c64c99a0fe882d22
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 9%

---

# Adobe Campaign 2023年环境升级 {#ac-system-upgrade}

Campaign基础架构依赖于第三方系统，必须定期更新最新版本和修复。 这些更新是强制性的，可确保服务的连续性，并保护Campaign环境免受安全风险的影响。 此外，还需要升级Campaign以确保与第三方系统更改兼容。

As a **托管或托管的Cloud Services客户**，则Adobe会在需要时通知您这些升级。 您将需要根据建议升级环境以确保合规性。

作为 **内部部署或混合客户**，则强烈建议您根据同一日历升级系统和Campaign版本。

出于安全考虑，您必须 [安装最新的Campaign内部版本](#ac-upgrade)，然后升级 [操作系统](#os-upgrade) 和/或 [关系数据库管理系统](#pg-upgrade).

>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。另请参阅 [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md).

## Campaign内部版本升级 {#ac-upgrade}

**您是否受影响？**

如果您受 [操作系统升级](#os-upgrade) 和/或 [数据库系统升级](#pg-upgrade) 下面详细说明，您必须将Campaign环境升级到 [最新7.3.2版本](../../rn/using/latest-release.md#release-7-3-2)，与这些系统兼容。

**如何更新？**

* 作为托管Cloud Services或托管客户，Adobe将与您联系并升级您的Campaign版本。
* 作为混合客户，Adobe将通知您中间源环境的计划内部版本升级日期。 您还必须将营销环境升级到该版本。
* 作为内部部署客户，系统会要求您将Campaign环境升级到最新的7.3.2内部版本。


## 操作系统升级 {#os-upgrade}

**您是否受影响？**

如果您在Debian操作系统上运行Campaign，要从最新的Debian安全更新中受益，您需要将Campaign基础架构移至 **Debian 11**. 请注意，Debian 9的安全支持将在2023年6月30日之前提供。

**如何更新？**

* 作为托管Cloud Services或托管客户，Adobe将与您联系并升级您的环境。
* 作为混合客户，Adobe将通知您中间源环境的计划升级日期。 如果您的营销环境也在Debian上运行，则还必须将其升级到Debian 11。
* 作为内部部署客户，系统会请您将环境升级到Debian 11。

## 数据库系统升级 {#pg-upgrade}

**您是否受影响？**

如果您的Campaign数据库系统是PostgreSQL，要从最新的PostgreSQL创新和安全更新中受益，您需要升级到 **PostgreSQL 14**. 请注意，PostgreSQL 11的生命周期将于2023年11月9日终止。

**如何更新？**

* 作为托管或托管的Cloud Services客户，Adobe将与您联系，并将数据库系统从PostgreSQL 11升级到PostgreSQL 14。
* 作为混合客户，如果您的营销数据库系统是PostgreSQL，则必须将其升级到PostgreSQL 14。
* 作为内部部署客户，系统会请您将数据库系统升级到PostgreSQL 14。


## 有用链接

* [升级环境](../../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [下载最新的Campaign Classic内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)
* [使新客户端控制台可供用户使用](../../installation/using/client-console-availability-for-windows.md)
